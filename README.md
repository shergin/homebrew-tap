# shergin/homebrew-tap

Homebrew formulae for [shergin](https://github.com/shergin)'s tools.

## kaz

[`kaz`](https://github.com/shergin/malevich/tree/main/cli) — pipe data to an
honest terminal plot (the CLI over [malevich](https://github.com/shergin/malevich)).

```sh
brew install shergin/tap/kaz
```

Or, to track `main`:

```sh
brew install --HEAD shergin/tap/kaz
```

The formula builds from source (needs a Rust toolchain, pulled in as a build
dependency) and installs the binary, shell completions, and the man page.

### Releasing a new version

1. Tag the CLI release on `shergin/malevich`, e.g. `git tag cli-vX.Y.Z && git push --tags`.
2. Update `Formula/kaz.rb` `url` and `sha256`:

   ```sh
   url="https://github.com/shergin/malevich/archive/refs/tags/cli-vX.Y.Z.tar.gz"
   curl -sL "$url" | shasum -a 256
   ```

3. `brew audit --strict --online shergin/tap/kaz` and
   `brew install --build-from-source shergin/tap/kaz` to verify, then commit.
