+++
title="How to use UV when you are used to PIP"
description="How to use UV explained easily"
summary="From installing to using UV as your venv and python manager in an existing pip project."
date="2026-06-18"
tags=["python", "pip", "uv"]
categories=["any", "tutorial", "dev", "devtools"]
+++

This post teach you how to use `uv` and my recommendations when migrating from
pip.

## How UV works

UV manages the python environment and version by itself. You dont need to
install any python version, it will install the version declared at
`.python-version` if needed or use your `$PATH` python.

UV will enter or create a `.venv` whenever you run `uv run` as needed and will
manage it for you.

UV will create a new one-time-use `venv` whenever you run `uvx`.

That way our project dependency stay clean and we avoid dependency conflicts.

## Setup development with UV

If you already have python in your OS or prefers to manage python versions with
another tool (like mise or asdf), UV will always try to use what you have in
your `$PATH` before trying to install a new version in your OS.

### Installing UV Standalone
The standalone `uv` installation is easier to upgrade if you're not tech savvy,
if you prefer to install via another package manager check
[the docs](https://docs.astral.sh/uv/getting-started/installation/).

#### Windows
On PowerShell run
```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/0.9.29/install.ps1 | iex"
```
If you see the error `The term 'uv' is not recognized as the name of a cmdlet`
reboot your OS.

Then check if it worked with
```powershell
uv self version
```

#### *nix (Mac/Linux)
With `curl` installed run
```sh
curl -LsSf https://astral.sh/uv/0.9.29/install.sh | sh;
```
then check if it worked with
```powershell
uv self version
```

### Upgrading UV Standalone
If you run `uv self update` and get a newer version make sure to
also bump uv versions on everywhere that mentions it in your project
(Dockerfile, ci, Docs)

#### Windows
```powershell
uv self update
```

#### *nix
It's recommended to add `UV_NO_MODIFY_PATH` to avoid changing the `$PATH` and
breaking something
```sh
UV_NO_MODIFY_PATH=1 uv self update
```

### Shell Autocompletion

#### Fish/Elvish/Others
Check the [Shell Autocompletion](https://docs.astral.sh/uv/getting-started/installation/#shell-autocompletion)
on uv docs.

#### PowerShell

##### UV
```powershell
if (!(Test-Path -Path $PROFILE)) {
  New-Item -ItemType File -Path $PROFILE -Force
}
Add-Content -Path $PROFILE -Value '(& uv generate-shell-completion powershell) | Out-String | Invoke-Expression'
```
##### UVX
```powershell
if (!(Test-Path -Path $PROFILE)) {
  New-Item -ItemType File -Path $PROFILE -Force
}
Add-Content -Path $PROFILE -Value '(& uvx --generate-shell-completion powershell) | Out-String | Invoke-Expression'
```
##### Zsh
```sh
echo 'eval "$(uv generate-shell-completion zsh)"' >> ~/.zshrc
```
```sh
echo 'eval "$(uvx --generate-shell-completion zsh)"' >> ~/.zshrc
```
then `source` the config
```sh
source ~/.zshrc
```
##### Bash
```sh
echo 'eval "$(uv generate-shell-completion bash)"' >> ~/.bashrc
```
```sh
echo 'eval "$(uvx --generate-shell-completion bash)"' >> ~/.bashrc
```
then `source` the config
```sh
source ~/.bashrc
```

### Using UV

When you run `uv run` or `uv tree` it automatically updates the lock and syncs.

If you do not have a venv yet the `uv sync` or `uv run` will create it for you.

If you do not have python yet uv will download it for you.

To update the project environment (venv) run
```sh
uv sync
```
To update the project lock file run
```sh
uv lock
```
To list the dependency tree
```sh
uv tree
```
To add a package with specific version
```sh
uv add "package~=1.2.3"
```
To add a dev only package with specific version
```sh
uv add --dev "package~=1.2.3"
```
To remove a package
```sh
uv remove package
```

Any package installed in the `pyproject.toml` that used to run with `python`
should use `uv`
```sh
uv run <command>
```
for example to run `pytest`
```sh
uv run pytest
```

Any packages that are **not** in the `pyproject.toml` should use `uvx`
```sh
uvx <command>
```
```sh
uvx ruff format
```
for tools like `ruff`, it's good to pin the latest version
```sh
uvx ruff@latest format
```

Inside Docker `uv` is also used
```sh
docker compose exec web uv run manage.py migrate
```

### Pip Migration

If you used the old `requirements.txt` and want to use `uv` it is recommended to
switch to the modern `pyproject.toml` as per the PEP 621. By default when you
run `uv add <package>` it will add it on a pyproject.toml as `dependencies`. For
developer only dependencies do `uv add --dev <package>`.

Since simple `requirements.txt` do not have dependency groups to differentiate
between dev and prod dependencies I recommend going through your
`requirements.txt` and assigning correctly which is what.

I always like to pin `dependencies` versions with `~=` that is the PEP 440
identifier for
[compatible releases](https://packaging.python.org/en/latest/specifications/version-specifiers/#compatible-release)
and pin `dev` dependencies with `>=` to use the latest.

This is an example of a project with `your-dependencies` and `pytest` installed
in their correct places.
```toml
[project]
name = "project-name"
version = "0.0.1"
description = "cool project"
readme = "README.md"
requires-python = "~=3.14.2"
dependencies = [
    "your-dependencies~=0.0.0",
]

[dependency-groups]
dev = [
    "pytest>=9.0.2",
]
```

#### Builtin ruff format support
`uv format` is a builtin alias to `ruff format` that is slightly faster because
it doesn't create a venv
```sh
uv format
```
same as
```sh
uvx ruff format
```

You can pass `ruff format` arguments to ruff by doing
```sh
uv format -- --line-length 80
```
same as
```sh
uvx ruff format --line-length 80
```

UV also have builtin support for the `--check` and `--diff` flags of
`ruff format`.

`ruff format` is a drop-in replacement for Black, `uv format --check` is the
equivalent of `black --check`.

`ruff check` is a drop-in replacement for Flake8, isort, pydocstyle, pyupgrade,
autoflake, and more.

Both commands are from ruff but behave completely different because
`ruff format --check` is running a code formatter without applying the format
while `ruff check` is running the linters as you configured in ruff.
```sh
uv format --check
```
same as
```sh
uv format -- --check
```
same as
```sh
uvx ruff format --check
```

The other `uv format` flags do not behave the same as `ruff format` flags and
are used to either configure uv itself or configure how `ruff format` needs to
behave in relation to uv.

