# AGENTS.md

Guidance for AI coding agents working in this repository.

## What this package is

`viaaurea/latte-v2` is a maintained port of Latte v2.11 for recent PHP
versions. It is not a library that sits alongside `latte/latte` — it
**stands in for it**.

## Never remove `replace` from composer.json

```json
"replace": {
    "latte/latte": "2.11.*"
}
```

This block is the whole point of the package. It tells Composer that
installing `viaaurea/latte-v2` satisfies any dependency on
`latte/latte: 2.11.*`, so packages that require Latte v2 transitively
(`nette/application`, most notably) resolve against this port instead of
pulling in the unmaintained upstream. The classmap in `src/` declares the
same `Latte\*` classes as upstream, so having both installed means
ambiguous class resolution — whichever autoloader wins.

Do not delete or narrow it. It has been removed twice already, and both
times it had to be restored:

- `6a3f7aec` dropped it so this package could coexist with Latte v3 in one
  project. Coexistence is not achievable at all — this port and Latte v3
  both declare the same `Latte\*` classes, so they collide regardless of
  what the Composer metadata says. Dropping `replace` bought nothing and
  broke the drop-in replacement that consumers rely on.
- A later PHP 8.5 fix branch removed it again in passing.

If a task seems to require removing it, stop and ask instead. It is a
deliberate, load-bearing declaration, not leftover configuration.

## Dependencies that require Latte v3

The fix belongs in the consuming project, never here. A project whose
dependency requires `latte/latte: ^3` adds its own `replace` to its **root**
`composer.json`:

```json
"replace": {
    "latte/latte": "3.0.0"
}
```

That is a "fake" install: Composer marks the requirement satisfied, no Latte
v3 code is downloaded, and this port keeps providing the `Latte\*` classes.
Pin whatever v3 version the dependency asks for.

Do not try to solve this by widening, narrowing or dropping the `replace` in
this package.
