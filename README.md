# PointLocate Helper — shareable Windows EXE

Made by **TechWithAndrew**. The credit is hardcoded into the app's small footer and the native EXE's company metadata.

Distribute **PointLocateHelper.exe** from `release-native/`. It is a single executable for **Windows 10/11, 64-bit**. Builders do not need Python, a separate support folder, a new server plugin, or a client mod. Third-party notices are embedded in the executable and also provided as a text file.

1. Open the EXE.
2. Keep Minecraft connected to your server with menus closed and the default **T** chat key.
3. Open the Google Earth Pro ruler or Google Earth Web measurement panel. The app reads length and heading automatically.
4. Enter the existing MDPointLocator point name. Click **Create point** or press **Ctrl+Alt+P**. It briefly switches to Minecraft, sends the plot command, and returns to Earth.

The Windows English OCR feature and the existing MDPointLocator server commands are required. Y height and block material remain configured in-game. See the main project README for the full usage notes.

## Source protection

This distribution compiles the application modules to native machine code with Nuitka. The payload is checked for Python source and bytecode files, and the compilation report verifies that the `pointhelper` modules were compiled. Docstrings and development launcher features are removed.

This makes recovering the original code substantially harder than extracting a normal Python bundle. It does **not** make reverse engineering impossible. Executable instructions, strings, resources, and runtime behavior can still be inspected. The single-file wrapper is packaging, not encryption, and embedded resources are extracted temporarily while the app runs.

Keep the workspace, Python source, compilation reports, generated C files, and `build/` directories private. Only the files under `release-native/` are intended to be shared. The SHA-256 file lets you compare exact builds; it is not a digital signature.

## Rebuild

The developer can run `build-native.ps1`. It installs the pinned compiler/build dependencies, runs the tests, compiles the native one-file EXE, checks both ruler fixtures, audits the payload, and copies only distribution files into `release-native/`.
