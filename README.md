# shergin/homebrew-tap

Homebrew formulae and casks for [shergin](https://github.com/shergin)'s tools.

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

## Caton

[Caton](https://github.com/shergin/caton) — a menu bar inbox for GitHub
notifications that shows only what needs you. Requires macOS 26.

```sh
brew install --cask shergin/tap/caton
```

Caton is not notarized, so macOS blocks its first launch: open System
Settings › Privacy & Security and click Open Anyway, once. `brew upgrade
--cask caton` installs updates; the app says when one is out.

### Releasing a new version

Run `./scripts/release.sh --publish` in the Caton repo after bumping the
version: it creates the GitHub Release and updates `Casks/caton.rb` here. See
[homebrew/README.md](https://github.com/shergin/caton/blob/main/homebrew/README.md).
