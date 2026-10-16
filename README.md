# ArmoredCreator RVC

Standalone repository for the ArmoredCreator voice-conversion (RVC) component.

## Goals

- Isolate voice conversion from ArmoredSpeech and ArmoredStudio dependencies.
- Keep RVC-specific Python dependencies documented separately.
- Validate the current Melody model and index with disposable audio before changing any working environment.
- Expose a small, stable integration boundary so Studio can invoke conversion without importing Speech internals.

## Safety and repository boundaries

- Do not commit Python virtual environments (`env/`, `.venv/`, `venv/`).
- Do not commit model weights (`.pth`), index files (`.index`), personal audio/video, generated outputs, credentials, or local environment files.
- Keep existing working RVC environments and original media untouched until a replacement environment passes validation.
- Do not assume Python 3.11 compatibility until a real conversion test passes.

## Current status

Initial repository scaffold. The implementation and dependency list must be added only after auditing the existing ArmoredStudio RVC wrapper and the installed RVC environment. No runtime or model files are tracked yet.

## Validation plan

1. Inventory the existing RVC wrapper, model location, and installed package versions.
2. Build a fresh isolated environment without modifying the existing environment.
3. Test imports and model/index discovery.
4. Convert a disposable WAV and verify the output file and audio properties.
5. Document the verified Python version and minimal dependency set.

## Windows

Use a dedicated virtual environment for this repository. Do not point the existing Studio runtime at this repository until the isolated conversion test passes.
