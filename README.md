# Common GHA workflows

## There are some implicit requirements for your service:

### Makefile:

It should have `install-dev` target, which installs all dependencies locally.

```bash
make install-dev
```

It should have `test` target, which runs all tests locally.


```bash
make test
```

It should have `set-version` target, which sets `${version}` of your service.

```bash
make set-version
```

which can be implemented as:

```bash
echo "__version__ = '${version}'" > app_dir/version.py
```

or

```bash
pip install poetry
poetry version ${version}
```

### Client library:

* `app_dir/schema` directory should contain your client code.
* `__version__` variable from `app_dir/version.py` file should be used as a client version.

### Other:

* `.pre-commit-config.yaml` file should be presented in the root of your repository.
