# JSON Translator

Fills in the blanks of a JSON translation file using Google Translate, in your
browser, without an API key.

Open a file, pick two languages, press Start. It works through the lines a few
at a time, waits when Google asks it to, and gives you the finished file back.

**Nothing is uploaded.** The file is read and written in the browser — the page
never sends it anywhere.

## What it is for

Most programs keep their words in a file like this, English on the left and the
translation on the right:

```json
{
  "Save": "Spara",
  "Add a printer": "Add a printer",
  "Bill {no} for {who}": "Bill {no} for {who}"
}
```

Lines that have not been translated yet have the English on both sides. This
finds those and fills them in, and leaves everything else alone — including any
wording you have already changed by hand.

## Why a page and not a script

Google's free endpoint answers a browser and refuses a server. A script running
on a machine somewhere gets `400` no matter how long it waits, because the
refusal is about who is asking. A page in a browser is a browser.

## Code inside braces stays code

`{name}` and `[code]` are the program talking to itself. A translator turns
`{how_much}` into `{hur mycket}` and then the program prints the braces instead
of a number.

So they are hidden before Google sees them, swapped for markers it will not
touch, and put back afterwards. There is a switch for each kind, because a file
may use one and not the other.

If a marker somehow comes back mangled, that line is left as it was — which is
always safe.

## Rate limits

Google stops answering after a few hundred lines from one address. When that
happens the page says so, waits, doubles the wait each time, and carries on.
Nothing is lost: the file is kept as it goes, and you can press Pause or Save
at any point and start again later with the part-finished file.

## Every pair as it lands

Each line appears on screen as it is translated, newest first, with the
original above it. If the tab dies you can still select and copy everything it
managed — a progress number gives you nothing to salvage.

**Copy them all as JSON** puts the finished pairs on the clipboard, in the
shape they came in.

## Running it

Two files, both standalone:

- `translate.html` — open it straight off your desktop, no server needed
- `translate.php` — the same page for a web host

Nothing to install and nothing to configure.

## A machine translation is a first draft

Short words are the ones it gets wrong, and short words are what buttons are
made of. Read it through before shipping it, or better, have somebody who
actually uses that kind of program read the screens.

## Licence

MIT.
