# TIBER v1.0.0

TIBER is an Android automation language and runtime designed for writing,
running, inspecting, and recording Android UI automation workflows.

This release provides the TIBER Windows runtime together with VS Code language
support.

## What's Included

```text
tiber.exe
    TIBER runtime for Windows x64

tiber-language-0.1.0.vsix
    VS Code language extension for TIBER

examples/
    Example TIBER scripts
```

## Requirements

- Windows x64
- An Android device or Android emulator
- ADB
- USB debugging enabled on the Android device

The TIBER runtime uses Android Debug Bridge (ADB) and UI automation to
communicate with Android devices.

## Installing the VS Code Extension

Open VS Code and install the included `.vsix` file.

### Using the command line

From the release directory:

```powershell
code --install-extension .\tiber-language-0.1.0.vsix
```

After installation, VS Code will provide syntax highlighting and language
support for TIBER files.

## TIBER File Types

TIBER supports the following file extensions:

```text
.tib
.tbr
.tiber
```

## Running a TIBER Script

Connect an Android device or start an Android emulator, then run:

```powershell
.\tiber.exe .\examples\hello.tib
```

To specify a particular device:

```powershell
.\tiber.exe --device DEVICE_ID .\examples\hello.tib
```

You can obtain connected device IDs with:

```powershell
adb devices
```

## Useful Commands

### Inspect Android UI Components

```powershell
.\tiber.exe --components
```

You can also inspect components from a TIBER file:

```powershell
.\tiber.exe --components .\examples\hello.tib
```

### Interactive Mode

Start the TIBER interpreter:

```powershell
.\tiber.exe --interpret
```

Write an interpreted session to a file:

```powershell
.\tiber.exe --interpret --write-to output.tib
```

### Record a Live Session

Record interactions with a connected Android device:

```powershell
.\tiber.exe --record-live recorded.tib
```

### Dry Run

Validate and execute a script in dry-run mode:

```powershell
.\tiber.exe --dry-run script.tib
```

### Verbose Output

```powershell
.\tiber.exe --verbose script.tib
```

### Run Part of a Script

Start execution from a labelled section:

```powershell
.\tiber.exe --start-from login script.tib
```

Stop execution before a labelled section:

```powershell
.\tiber.exe --end-before cleanup script.tib
```

Both options can be used together:

```powershell
.\tiber.exe --start-from login --end-before cleanup script.tib
```

## Example TIBER

A basic TIBER script can interact with Android UI elements:

```tib
login.username.click()
login.username.input("kanish")
```

The exact selectors and commands available depend on the application UI and
the TIBER script being used.

## UI Components

TIBER can inspect the Android UI hierarchy and expose components that can be
used by automation scripts.

For example, a component may be represented by a TIBER resource identifier:

```tib
textbox
```

A component can then be interacted with through the corresponding TIBER
syntax.

## Recording

TIBER can record interactions with an Android device and generate a TIBER
script:

```powershell
.\tiber.exe --record-live recorded.tib
```

The resulting file can be opened in VS Code using the included TIBER language
extension.

## Examples

Example scripts are included in the `examples` directory.

```text
examples/
├── hello.tib
├── login.tib
└── device-info.tib
```

These examples are intended as starting points for creating your own TIBER
automation scripts.

## Command Reference

```text
tiber [options] [file]

Options:

  --version
      Display the TIBER version.

  --device DEVICE
      Select an Android device.

  --dry-run
      Run without performing device actions.

  --verbose
      Enable verbose output.

  --live
      Enable live execution.

  --live-cache SECONDS
      Configure live UI cache duration.

  --start-from LABEL
      Start execution from a labelled section.

  --end-before LABEL
      Stop execution before a labelled section.

  --interpret
      Start the interactive TIBER interpreter.

  --write-to FILE
      Write interpreted or generated output to a file.

  --record-live FILE
      Record a live Android interaction session.

  --input-device PATH
      Specify an input device.

  --log-to FILE
      Write runtime logs to a file.

  --components [FILE ...]
      Inspect Android UI components.
```

## Version

**TIBER Runtime:** 1.0.0

**TIBER VS Code Language Support:** 0.1.0

**Platform:** Windows x64

## License

The TIBER runtime and associated components may contain software distributed
under their respective licenses.

See `LICENSE.md` for the licensing information applicable to this release.

## Copyright

Copyright © 2026 Kanish Shanmuga R.

Distributed by Oryvex.
