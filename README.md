
# Py2Debv2

**Py2Debv2** by **Avi Twil** from **Twil Industries**  
A powerful Python packaging tool that converts Python scripts into Debian packages (`.deb`) or standalone executables with full dependency management.

---

## Overview

**Py2Debv2** allows you to:

- Package Python scripts into Debian `.deb` packages.
- Automatically detect Python dependencies.
- Include dependencies inside a standalone binary (via Nuitka) or leave them managed by the system.
- Create optional `install.sh` setup scripts.
- Generate `tar.gz` archives containing the `.deb` and setup script.
- Add man pages for easy command-line help.

**Key advantage:** Simplifies distribution of Python scripts on Debian-based systems, eliminating manual packaging steps while ensuring portability and dependency management.

---

## Installation

### Using Prebuilt DEB Package

1. Clone the repository:

```bash
git clone https://github.com/avitwil/py2debv2.git
cd py2debv2
````

2. Install the package:

```bash
sudo dpkg -i py2debv2.deb
```

3. Run the command directly:

```bash
py2debv2 --help
```

### Using Setup Script

```bash
sudo ./install.sh
```

This will install the command globally under `/usr/local/bin/`.

### From Source (Optional)

If you prefer, you can run the Python script directly:

```bash
python3 py2debv2.py <python_file> --command <cmd_name> -cn "Avi Twil" -email "unknown@example.com"
```

> Recommended only for development or testing. Use the prebuilt package for deployment.

---

## Usage Examples

### Basic Debian Package

```bash
py2debv2 my_script.py --command mytool -cn "Avi Twil" -email "avitwil@example.com"
```

### Create Setup Script and TAR.GZ Archive

```bash
py2debv2 my_script.py --command mytool --setup --tar-gz -cn "Avi Twil"
```

### Compile as Standalone Binary (with dependencies included)

```bash
py2debv2 my_script.py --command mytool --bin --setup
```

### Add a Man Page

```bash
py2debv2 my_script.py --command mytool -man my_tool.1
```

---

## Advantages Over Similar Tools

| Feature                        | Py2Debv2 | dh-virtualenv | PyInstaller | py2deb |
| ------------------------------ | -------- | ------------- | ----------- | ------ |
| Debian `.deb` Packaging        | ✅        | ✅             | ❌           | ✅      |
| Automatic dependency detection | ✅        | ❌             | ❌           | ✅      |
| Standalone binary option       | ✅        | ❌             | ✅           | ❌      |
| Optional `tar.gz` archive      | ✅        | ❌             | ❌           | ❌      |
| Optional man page integration  | ✅        | ❌             | ❌           | ❌      |
| Easy setup script generation   | ✅        | ❌             | ❌           | ❌      |

**Summary:** Py2Debv2 combines packaging flexibility, dependency management, and standalone binary creation in one tool, offering a more complete solution than competitors for Debian-based systems.

---

## License

Py2Debv2 is released under the **MIT License**. See the `LICENSE` file for details.

---

## Author

**Avi Twil**
**Twil Industries**


