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

## Load from web

The library has a **🌐 Load from web** button: pick a source (NovelFull or
AllNovelFull), search for a novel, then import a chapter range (up to 150
chapters at a time). The imported chapters are packed into a real EPUB file in
your browser and opened like any other book — table of contents, read-aloud and
saved reading position all work. Long novels load their chapter list lazily, so
you can import chapter 500 just as easily as chapter 1.

The fetch goes through public CORS proxies (the first one that answers is used
for the rest of the session). Import depends on those proxies and on the source
sites staying reachable.

## Shared passcode

The page has a basic shared-passcode screen. It is only a casual deterrent: the
verifier runs in the browser, and visitors can bypass the screen or access EPUB
files directly. It does not provide private accounts, admin approval, or secure
file access. The unlock is remembered for the current browser tab only.
