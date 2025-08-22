

# Py2DebV2

![Py2DebV2 Logo](https://via.placeholder.com/600x150?text=Py2DebV2)

**Py2DebV2** is a Python utility designed to automatically create Debian (`.deb`) packages from Python scripts. It detects Python dependencies, optionally compiles standalone binaries using Nuitka, and can generate setup scripts, tar.gz archives, and man pages for easy distribution.

---

## Features

* Convert Python scripts into Debian `.deb` packages.
* Automatically detect Python dependencies and map them to Debian packages.
* Optionally compile scripts into standalone binaries using Nuitka.
* Generate `install.sh` setup scripts.
* Create `tar.gz` archives containing the DEB and setup script.
* Include man pages for installed commands.
* Supports automatic inclusion of dependencies inside standalone binaries.

---

## Installation

Before using `py2debv2`, install required dependencies:

```bash
sudo apt update
sudo apt install python3 python3-venv python3-pip dpkg-dev
pipx install nuitka
```

Clone this repository:

```bash
git clone https://github.com/avitwil/py2debv2.git
cd py2debv2
```

Make the script executable:

```bash
chmod +x py2debv2.py
```

---

## Usage

### Basic DEB Packaging

```bash
./py2debv2.py <python_file> --command <command_name> -cn "Creator Name" -email "creator@example.com"
```

Example:

```bash
./py2debv2.py myscript.py --command mytool -cn "Avi Twil" -email "avitwil@example.com"
```

### Create DEB with Setup Script

```bash
./py2debv2.py myscript.py --command mytool --setup
```

### Create tar.gz Archive

```bash
./py2debv2.py myscript.py --command mytool --setup --tar-gz
```

### Compile Standalone Binary (Includes Dependencies)

```bash
./py2debv2.py myscript.py --command mytool --bin
```

### Include a Man Page

```bash
./py2debv2.py myscript.py --command mytool -man mytool.1
```

---

## Options

| Option                    | Description                                             |
| ------------------------- | ------------------------------------------------------- |
| `<python_file>`           | Python script to package (required)                     |
| `-cn <creator_name>`      | Name of the package creator (required)                  |
| `-email <creator_email>`  | Email of the creator (required)                         |
| `--command <name>`        | Command name for the installed executable (required)    |
| `--sudo`                  | Add `sudo` to package dependencies                      |
| `--setup`                 | Create a setup installation script                      |
| `--tar-gz`                | Create a tar.gz archive containing DEB and setup script |
| `--bin`                   | Compile as standalone binary with dependencies included |
| `-man, --man_page <file>` | Add man page for the command                            |
| `-h, --help`              | Show this help menu                                     |

---

## Dependency Detection

`py2debv2` automatically parses your Python script for import statements and detects external libraries such as:

```
colorama, pyfiglet, tqdm, requests, numpy, pandas, matplotlib, flask, django, Pillow, etc.
```

For standard Python modules, it ignores them automatically.

---

## Output Files

* `/usr/local/bin/<command_name>` → Installed Python script or binary.
* `/usr/share/man/man1/<command_name>.1.gz` → Installed man page (if provided).
* `install.sh` → Optional setup script for DEB installation.
* `<command_name>.deb` → Generated Debian package.
* `<command_name>.tar.gz` → Optional archive containing DEB and setup script.

---

## Author

**Avi Twil**
Twil Industries

---

## License

This project is released under the MIT License.

