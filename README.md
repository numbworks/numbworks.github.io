# numbworks.github.io

Contact: numbworks@gmail.com

## Introduction

This is a custom Python Package Index for nw* packages.

|||
|:---|:---|
|URL|https://numbworks.github.io|
|Repository URL|https://github.com/numbworks/numbworks.github.io/|

## Getting started

To install packages, open a Terminal application and run one of the following commands:

- `pip install --extra-index-url https://numbworks.github.io {package_name}`
- `pip install --extra-index-url https://numbworks.github.io {package_name}=={version}`

To install the latest versions:

- `pip install --extra-index-url https://numbworks.github.io nwpackageversions`
- `pip install --extra-index-url https://numbworks.github.io nwshared`
- `pip install --extra-index-url https://numbworks.github.io nwtimetracking`
- `pip install --extra-index-url https://numbworks.github.io nwreadinglist`

If you want to try it out in a Docker container instead of your local machine, create one and login into it first:

- `docker run -it python:3.12.5-bookworm /bin/bash`

## Appendix - The link format

These commands work in the Terminal and in the index.html:

```
pip install 'git+https://github.com/numbworks/nwpackageversions.git@v1.8.1#subdirectory=src&egg=nwpackageversions-1.8.1'
pip install 'git+https://github.com/numbworks/nwpackageversions.git@v1.8.0#subdirectory=src&egg=nwpackageversions-1.8.0'
...
```


These commands work in the Terminal but **not in the index.html**:

```
pip install 'git+https://github.com/numbworks/nwpackageversions.git@v1.8.1#egg=nwpackageversions&subdirectory=src'
pip install 'git+https://github.com/numbworks/nwpackageversions.git@v1.8.0#egg=nwpackageversions&subdirectory=src'
...
```

I guess that this is due of this specific requirement in PEP 503: *"[...] the text of the anchor tag MUST match the final path component (the filename) of the URL [...]"*.

## Sources
- [PEP 503 – Simple Repository API](https://peps.python.org/pep-0503/)
- [How to use GitHub as a PyPi server - Tutorial](https://www.freecodecamp.org/news/how-to-use-github-as-a-pypi-server-1c3b0d07db2/)
- [How to use GitHub as a PyPi server - Repository](https://github.com/ceddlyburge/python-package-server/tree/master)

## Other links

- [LICENSE](LICENSE)