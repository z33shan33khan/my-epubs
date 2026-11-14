# my-epubs
Books and Novels reader

## Repository covers

Embedded covers for the books in `books/` are stored in `covers/` and mapped by
`covers/manifest.json`. To save a cover from another EPUB, open Settings, choose
the repository's `covers/` folder, then select **Detect and save cover**. The
reader writes the image and updates the manifest in that folder; commit those
changes to keep them in the repository. The folder picker is supported in
Chromium-based browsers on HTTPS or localhost. The selected files stay on your
device and are not uploaded by the reader.

## Shared passcode

The page has a basic shared-passcode screen. It is only a casual deterrent: the
verifier runs in the browser, and visitors can bypass the screen or access EPUB
files directly. It does not provide private accounts, admin approval, or secure
file access. The unlock is remembered for the current browser tab only.
