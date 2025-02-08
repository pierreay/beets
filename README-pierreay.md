# About

This is a development repository for [Beets](https://github.com/beetbox/beets/).
Normally managed using `poetry`, in my case, I will manually manage it using `venv` and `pipx`.

# Installation for usage

We will use `pipx` that will create a virtual environment for us.

1. Perform a local clone of repository in a directory:

```bash
mkdir -p ~/.local/src && git clone https://github.com/pierreay/beets ~/.local/src/beets
```

2. Checkout my development branch containing my patches:

```bash
cd ~/.local/src/beets && git checkout dev
```

3. Perform a static installation using `pipx`:

```bash
pipx install .
```

4. Manually install the missing dependencies into the virtual environment:

```bash
# For `beet` core:
pipx inject beets pygobject
# For `chroma` plugin:
pipx inject beets pyacoustid
# Fix `ModuleNotFoundError: No module named 'aifc'` error thrown by `audioread` on Python 3.13:
# See:
# https://github.com/beetbox/audioread/issues/144
# https://github.com/beetbox/audioread/pull/145
# https://github.com/youknowone/python-deadlib
pipx inject beets standard-aifc standard-sunau
# For `lyrics` plugin:
pipx inject beets langdetect bs4
```

Since it is not packaged by a distribution, the shell completions are not installed by default.
Therefore, we manually symlink the ZSH completions from the repository to loaded Oh-My-ZSH completions:

```bash
ln -s ~/.local/src/beets/extra/_beet ~/.cache/oh-my-zsh/completions/_beet
```

# Installation for developing

We will use `venv` to manage a virtual environment inside the development repository.


1. Perform a local clone of repository in a directory:

```bash
mkdir -p ~/.local/src && git clone https://github.com/pierreay/beets ~/.local/src/beets
```

2. Checkout my development branch containing my patches:

```bash
cd ~/.local/src/beets && git checkout dev
```

3. Create a virtual environment inside the development repository and activate it:

```bash
python -m venv beets-venv
source beets-venv/bin/activate
```

4. Manually install the missing dependencies into the virtual environment:

```bash
# For `beet` core:
pip install pygobject
# For `chroma` plugin:
pip install pyacoustid
# Fix `ModuleNotFoundError: No module named 'aifc'` error thrown by `audioread` on Python 3.13:
# See:
# https://github.com/beetbox/audioread/issues/144
# https://github.com/beetbox/audioread/pull/145
# https://github.com/youknowone/python-deadlib
pip install standard-aifc standard-sunau
# For `lyrics` plugin:
pip install langdetect bs4
```

5. Install Beets into the virtual environment:

```bash
pip install -e .
```

Since it is not packaged by a distribution, the shell completions are not installed by default.
Therefore, we manually symlink the ZSH completions from the repository to loaded Oh-My-ZSH completions:

```bash
ln -s ~/.local/src/beets/extra/_beet ~/.cache/oh-my-zsh/completions/_beet
```
