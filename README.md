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

## Load from disk

The library has a **📁 Load from disk** button that opens a file picker:

- **EPUB** files open directly.
- **PDF** files are read page by page (via PDF.js, loaded on demand) and split
  into chapters at "Chapter/Part/Prologue" headings.
- **TXT / Markdown** files become chapters at `#` headings or "Chapter N"
  markers, or are split into ~7000-character parts when there are none.
- **HTML** pages are stripped to their readable text and split at `<h1>/<h2>`.
- **DOCX** files are unpacked in the browser (JSZip) and split at heading-1 /
  title paragraphs.
- **FB2** files (plain or `.fb2.zip`, UTF-8 or Windows-1251) become chapters at
  their `<section>` titles.

Everything except a raw EPUB is converted into a real EPUB in the browser (the
same builder the web import uses), so the table of contents, read-aloud and
saved reading position all work unchanged. Uploaded books are remembered in
IndexedDB and appear at the front of the library with a 📁 badge and an ×
button to remove them (the file on your disk is never touched). Re-uploading
the same title replaces the old entry instead of duplicating it.

Scanned/image-only PDFs have no extractable text and are not supported.

## Shared passcode

The page has a basic shared-passcode screen. It is only a casual deterrent: the
verifier runs in the browser, and visitors can bypass the screen or access EPUB
files directly. It does not provide private accounts, admin approval, or secure
file access. The unlock is remembered for the current browser tab only.
