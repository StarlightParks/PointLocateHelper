# Version 2 verification

The simplified app uses automatic local ruler capture and a brief Minecraft focus switch. It does not use the v1 bridge.

- 33 Python tests pass, including native Windows OCR against both exact user-supplied PNGs.
- Web screenshot: **199.99 m**, **359.66°**.
- Pro screenshot: **210.09 m**, **0.09°**, using Map Length rather than 210.08 Ground Length.
- Tests cover full-window map-scale noise, incomplete/invalid readings, plot-command formatting, input rejection, selecting a game instead of a launcher, multiple game windows, focus refusal, interrupted focus, restoring a minimized game, and returning to Earth.
- The compact app automatically detected the live Earth Pro Ruler dialog without a selected region and displayed **210.09 m / 0.09°**.
- The packaged executable's OCR check read both supplied images correctly, confirming that the Windows OCR runtime and its metadata are included in the distribution.
- Focus-switch sender tests use a fake input adapter; they do not place blocks or send chat on the live server.
- An additional native Windows input check sent the exact `/point plot testPoint 210.09 0.09` string to a local test window and verified focus returned to its companion test window. No Minecraft input was involved in this check.

The Minecraft sender uses the default T chat key. It requires an online player in the game world with menus closed and an existing MDPointLocator point. Sending the command and server acceptance are separate: the app reports only **Command sent**. A live placement on the user's server has not been performed by the agent.

## Native single-file distribution

- `build-native.ps1` produced the standalone `release-native/PointLocateHelper.exe` using Nuitka 4.3.5 and Zig, with no Python installation required on the receiving Windows x64 PC.
- All 33 tests passed before compilation. The final EXE correctly read both supplied ruler images through its packaged Windows OCR runtime.
- The one-file EXE was launched from the Windows temporary directory to check independence from the project folder. Its multiprocessing background reader successfully read the live Earth Pro ruler as **175.77 m / 3.37°**.
- The compilation report lists all eight `pointhelper` package/modules as compiled. The executable payload contains no `.py`, `.pyc`, or `.pyo` files. Source files, generated C, and build reports remain outside the shareable distribution.
- The latest EXE's SHA-256 is recorded in `release-native/PointLocateHelper.sha256`.
- Opened the final single-file GUI from outside the project folder and confirmed its automatic live ruler values, fonts, settings, and command preview rendered correctly.

Native compilation raises the effort needed to recover the code; it does not make reverse engineering impossible. See DISTRIBUTION.md.
