# new_pico

A shell script that helps setup a clean Raspberry Pi Pico C/C++ projects for Visual Studio Code under Linux.


## 🚀 What It Does

- Clones a Pico project template
- Renames internal references
- Initializes a fresh Git repo
- Verifies the Raspberry Pi Pico SDK is available and in the correct path
- Configures the build system (CMake)
- Opens the project in VSCode

## 📦 Requirements

### Distribution-dependent 

- cmake
- gcc-arm-none-eabi 
- libnewlib-arm-none-eabi (or equivalent)
- libusb-1.0-0-dev
- pkg-config

### Other

- A C/C++ compiler installed and configured correctly. (arm-none-eabi-gcc may require attention)
- (Raspberry Pi Pico SDK installed *NO LONGER REQUIRED*) 
The tool checks availability of the SDK and if not available clones it to the directory set in `new_pico.cfg`
- VSCode installed
- Template repo available at `~/Projects/pico-project-template` (or modify the script to point elsewhere)
- `new_pico.cfg` A basic configuration file (described below) 

## 🔧 Usage

```bash```

`./new_pico <project_name>`
### Options

| Flag               | Short | Description                                 |
|--------------------|-------|---------------------------------------------|
| `--help`           | `-h`  | Show this help text                         |
| `--use_c`          | `-c`  | Use C instead of C++ for the project        |
| `--force`          | `-f`  | Force cloning the git repository even       |
|                    |       |  it exists.                                 |
| `--no_vscode`      | `-n`  | Do not launch Visual Studio Code            |
| `--no_sdk_check`   | `-s`  | Do not check and install the SDK            |
| `--template_path`  | `-t`  | Set an alternative template path            |

## 🔧 Files

`new_pico.cfg`

### Variables
| Name            | Description                         | Default |
|-----------------|-------------------------------------|----------
| TEMPLATE_REPO   | github repository                   |         |
| TEMPLATE_CACHE  | local template repository directory |         |
| TEMPLATE_FOLDER | name of the product directory       |         |
| PICO_SDK_PATH   | path to the Raspberry Pi Pico SDK   |         |
| SDK_AUTOLOAD    | check the SDK exists or clone it    |    true |
| USE_CPP         | use C++ (on) or C (off)             |    true |
| LAUNCH_VSCODE   | launch VSCode with the project      |    true |
| FORCE_CLONE     | reload the github repo              |   false |
| README_INFO     | The text for the new README.md file |   false |

## 🔧 Workflow example

# Step 1. Create a new project
```
new_pico blink_test
```

"blink_test" is just an example name.

# Step 2. Build the projects
```
cd blink_test
cmake -S . -B build
cmake --build build
```

# Step 3. Put the compiled file on the RPi 2040 device
Connect the RPi 2040 device via USB and hold the BOOTSEL switch
```
build/blink_test.uf2 /media/$USER/RPI-RP2/
```

"/media/$USER/RPI-RP2" is just an example path for the directory.
