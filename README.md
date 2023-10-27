# Bug in `--import` order

1. Run the following command:

```sh
$ node --import ./a.mjs --import ./b.mjs main.mjs
a...
b...
```

The output here makes sense, as the order of execution of `a.js` and `b.js` is first `a` then `b`

2. Go to `a.js` and uncomment the first line (with `import './sub.mjs`). Note that `sub.mjs` is an empty file.

Now run the same command again:

```sh
$ node --import ./a.mjs --import ./b.mjs main.mjs
b...
a...
```

This doesn't make sense.
