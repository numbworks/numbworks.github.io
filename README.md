# NW's Software Hub

Contact: numbworks@gmail.com

## Introduction

This is the landing page for **NW's Software Hub**, which consists of the following services:

|||
|:---|:---|
|NW's Binary Releases|https://numbworks.github.io/binaries|
|NW's Python Package Index|https://numbworks.github.io/pypi|

## NW's Binary Releases

### Target Platforms

My applications are compiled for the following platforms:

- Windows (x64)
- Linux
  - generic-amd64
  - generic-arm64
  - debian-amd64
  - debian-arm64

As an open‑source developer, I don’t target Apple MacOS.

The reasons are:

- Paid certification: distributing binaries requires an annual developer license, which is incompatible with free software distribution.
- Expensive hardware: building and testing MacOS apps requires proprietary Apple hardware with a high entry cost and a closed ecosystem.
- Lack of open‑source investment: Apple is not among the companies that actively support open‑source projects with funding or engineering resources.
- No local cross‑compilation: Python applications cannot be cross‑compiled for MacOS from Linux or Windows, breaking my unified build workflow.

If you are a MacOs user, you can still attempt to compile or run my applications from the source code.

## NW's Python Package Index

### Getting started

To install packages, open a Terminal application and run one of the following commands:

- `pip install --extra-index-url https://numbworks.github.io/pypi {package_name}`
- `pip install --extra-index-url https://numbworks.github.io/pypi {package_name}=={version}`

To install the latest versions:

- `pip install --extra-index-url https://numbworks.github.io/pypi nwpackageversions`
- `pip install --extra-index-url https://numbworks.github.io/pypi nwtimetracking`
- `pip install --extra-index-url https://numbworks.github.io/pypi nwreadinglist`

If you want to try it out in a Docker container instead of your local machine, create one and login into it first:

- `docker run -it python:3.12.5-bookworm /bin/bash`

### The Link Format

These commands work in the Terminal and in the index.html:

```sh
pip install 'git+https://github.com/numbworks/nwpackageversions.git@v1.8.1#subdirectory=src&egg=nwpackageversions-1.8.1'
pip install 'git+https://github.com/numbworks/nwpackageversions.git@v1.8.0#subdirectory=src&egg=nwpackageversions-1.8.0'
...
```

These commands work in the Terminal but **not in the index.html**:

```sh
pip install 'git+https://github.com/numbworks/nwpackageversions.git@v1.8.1#egg=nwpackageversions&subdirectory=src'
pip install 'git+https://github.com/numbworks/nwpackageversions.git@v1.8.0#egg=nwpackageversions&subdirectory=src'
...
```

I guess that this is due of this specific requirement in PEP 503: *"[...] the text of the anchor tag MUST match the final path component (the filename) of the URL [...]"*.

### Dynamic index.html pages

Dynamically-generated index.html pages for packages do display perfectly on GitHub Pages, but they don't work with `pip install`:

```html
<!DOCTYPE html>
<html>
  <head>
    <script>
	
      const packageName = "nwtimetracking";
      const versions = ["5.0.0", "4.8.0", "4.7.0", "4.6.0", "4.5.0", "4.0.0"];

      function initializePage() {
        document.title = packageName;

        const header = document.createElement("h1");
        header.textContent = packageName;
        document.body.prepend(header);

        const container = document.getElementById("links-container");
        versions.forEach(version => {
          const link = document.createElement("a");
          link.href = `git+https://github.com/numbworks/${packageName}.git@v${version}#subdirectory=src&egg=${packageName}-${version}`;
          link.dataset.requiresPython = ">=3.12.5";
          link.textContent = `${packageName}-${version}`;

          const lineBreak = document.createElement("br");

          container.appendChild(link);
          container.appendChild(lineBreak);
        });
      }

      window.onload = initializePage;
    </script>
  </head>
  <body>
    <div id="links-container"></div>
  </body>
</html>
```

### Sources
- [PEP 503 – Simple Repository API](https://peps.python.org/pep-0503/)
- [How to use GitHub as a PyPi server - Tutorial](https://www.freecodecamp.org/news/how-to-use-github-as-a-pypi-server-1c3b0d07db2/)
- [How to use GitHub as a PyPi server - Repository](https://github.com/ceddlyburge/python-package-server/tree/master)

## Other links

- [LICENSE](LICENSE)