
# Py2Debv2

**Py2Debv2** is a Python utility for automatically creating Debian (`.deb`) packages from Python scripts. It simplifies packaging by handling dependencies, optional standalone binaries, man pages, and setup scripts—all in one tool.

---

## Features

- Automatically detect Python dependencies and map them to Debian packages.
- Optional standalone binary compilation using Nuitka (`--bin` flag).
- Create setup installation scripts (`--setup` flag).
- Man page integration (`--man` flag).
- Bundle DEB and setup scripts into a `tar.gz` archive (`--tar-gz` flag).
- CLI-friendly with progress bars for compilation and dependency inclusion.
- Supports multiple dependencies automatically.
- Fully automates `.deb` packaging for Python scripts.

---

## Installation

### From `.deb` package

If you have the `.deb` package ready:

```bash
sudo dpkg -i py2debv2.deb
sudo apt-get install -f  # Install missing dependencies if needed
````

### From `tar.gz` archive

```bash
tar -xzf py2debv2.tar.gz
cd py2debv2
sudo ./install.sh
```

After installation, the `py2debv2` command is available system-wide.

---

## Usage Examples

### Basic `.deb` package

```bash
py2debv2 myscript.py --command myscript -cn "Avi Twil" -email "avitwil@example.com"
```

### Standalone binary compilation

```bash
py2debv2 myscript.py --command myscript --bin --setup
```

### Including a man page

```bash
py2debv2 myscript.py --command myscript --man myscript.1
```

### Creating tar.gz archive

```bash
py2debv2 myscript.py --command myscript --tar-gz --setup
```

---

## Comparison with Similar Tools

| Feature / Tool                      | Py2Debv2        | fpm (Effing Package Manager) | PyInstaller | Nuitka Standalone |
| ----------------------------------- | --------------- | ---------------------------- | ----------- | ----------------- |
| Debian `.deb` Packaging             | ✅               | ✅                            | ❌           | ✅                 |
| Automatic Python deps mapping       | ✅               | ❌                            | ❌           | ❌                 |
| Standalone binary option            | ✅ (`--bin`)     | ❌                            | ✅           | ✅                 |
| Tar.gz archive option               | ✅ (`--tar-gz`)  | ❌                            | ❌           | ❌                 |
| Man page integration                | ✅ (`--man`)     | ❌                            | ❌           | ❌                 |
| Easy setup script generation        | ✅ (`--setup`)   | ❌                            | ❌           | ❌                 |
| Supports multi-dependency detection | ✅               | ❌                            | ❌           | ❌                 |
| Cross-platform support              | Partial (Linux) | ✅                            | ✅           | Partial           |
| CLI & terminal friendly             | ✅ CLI           | CLI only                     | CLI only    | CLI only          |
| Installation via `.deb`             | ✅               | ✅                            | ❌           | ✅                 |

**Advantages of Py2Debv2:**

* Fully automates dependency detection and mapping to Debian packages.
* Supports optional standalone binaries for easier distribution.
* Can generate man pages and setup scripts automatically.
* Can bundle DEB and setup scripts into a tar.gz archive for convenient distribution.
* Designed specifically for Python scripts, making it simpler than general-purpose packagers like `fpm`.

---

## License

MIT License – see `LICENSE` file for details.


