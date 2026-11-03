# legaled.github.io

The personal CV site of **Christopher Elias**, Senior Data Engineer and qualified solicitor. It's styled as a retro terminal.

**Live site:** https://legaled.github.io/

## Usage

When the page loads, it types out a start-up message and then opens a terminal prompt. Type these commands:

| Command | What it does |
|---------|--------------|
| `help`  | Lists all available commands |
| `cv`    | Opens the CV: skills chart, job history and "Why me?" |
| `hello` | Says hi |

## How it works

It's a static site served by GitHub Pages. There's no build step and no images: all graphics are made with CSS and ASCII art.

| File | Purpose |
|------|---------|
| `index.html` | Page layout, ASCII banner, typewriter intro and terminal command registration |
| `cv.html` | CV content, fetched and shown in a Bootstrap modal by the `cv` command. The skills chart is drawn with D3 v3 |
| `ptty.jquery.js` | The [Ptty](https://gitlab.com/pachanka/ptty) jQuery terminal emulator. This is the copy from Ptty's live site, because the official release has a bug that leaves `help` without its command list |
| `terminal.css`, `bootstrap.css` | Terminal and dark Bootstrap themes |
| `terminal.js` | An alternative vanilla-JS terminal implementation (not currently loaded) |

### Adding a command

Register it in `index.html`, inside `terminalUp()`:

```js
$ptty.register('command', {
  name: 'mycommand',
  method: function (cmd) {
    cmd.out = 'output text or HTML';
    return cmd;
  },
  options: [],
  help: 'Description shown by the help command.'
});
```

## Running locally

`cv.html` is loaded with `fetch`, which won't work over `file://`, so serve the folder:

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

## To do

- [ ] Add padding between the init line and the terminal box
- [ ] Make the ASCII art banner responsive (it doesn't fit on phones)
- [ ] Replace the placeholder in the CV with a zoomable sunburst of skills ([example](https://observablehq.com/@d3/zoomable-sunburst))
- [ ] Refactor and tidy up comments

## Credits

These projects inspired the site:
- [Ptty](https://gitlab.com/pachanka/ptty)
- [andersevenrud/shell](http://andersevenrud.github.io/shell/)
- [Termynal](https://github.com/ines/termynal)
- [terminal.css](https://terminalcss.xyz/)

## Contact

chris@deltaregulation.com · [GitHub](https://github.com/LegalEd)
