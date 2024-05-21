# check-python-exists

This is a basic wrapper around the GHA provided `actions/setup-python` that:
1. [avoids the issue with requiring `sudo`][1] and having [`/Users/runner/hostedtoolcache` on the self hosted runner][2].
2. Add support for Windows/ARM64 until [it is fixed upstream][3].

- If `is-self-hosted: false` then this falls back to `actions/setup-python` at v5.0.0.
- If `python-version` is provided, that takes precedence over any existing `.python-version` files
- If running on Windows/arm64, uses a hack hardcoded for 3.11.
- If you need to point to a different `.python-version` file, pass the path relative to the current working directory to the `python-version-file` parameter.

[1]: https://github.com/actions/runner-images/issues/7987
[2]: https://github.com/actions/setup-python/blob/main/docs/advanced-usage.md#macos
[3]: https://github.com/actions/setup-python/issues/715
