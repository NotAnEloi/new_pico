# new_pico

A shell script that helps setup a clean Raspberry Pi Pico C/C++ projects for Visual Studio Code under Linux.


## 🚀 What It Does

- Clones a Pico project template
- Renames internal references
- Initializes a fresh Git repo
- Configures the build system (CMake)
- Opens the project in VSCode

## 📦 Requirements

- Raspberry Pi Pico SDK installed
- VSCode installed
- Template repo available at `~/Projects/pico-project-template` (or modify the script to point elsewhere)

## 🔧 Usage

```bash
./new_pico <project_name>
### Options

| Flag               | Alias | Description                                 |
|--------------------|-------|---------------------------------------------|
| `--help`           | `-h`  | Show this help text                         |
| `--use_c`          | `-c`  | Use C instead of C++ for the project        |
| `--no_vscode`      | `-n`  | Do not launch Visual Studio Code            |
| `--template_path`  | `-t`  | Set an alternative template path            |
