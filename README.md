# hugo-deskcrew

![DeskCrew widget for Hugo](https://deskcrew.io/packages/deskcrew-hugo.gif)

A Hugo theme component that adds the [DeskCrew](https://deskcrew.io) support widget to every page: live chat, AI answers grounded in your knowledge base, and a help center. One partial, configured from `hugo.toml`.

You need a free DeskCrew account to get a widget key: https://deskcrew.io/signup

## Install

As a Hugo module:

```
hugo mod get github.com/webmilmind1/hugo-deskcrew
```

```toml
# hugo.toml
[module]
  [[module.imports]]
    path = "github.com/webmilmind1/hugo-deskcrew"

[params.deskcrew]
  key = "pub_your_widget_key" # from your DeskCrew dashboard, Install page
  board = "your-board"        # optional
  # color = "#4f46e5"         # optional, 6-digit hex
  # position = "right"        # optional, or "left"
  # greeting = "Hi! How can we help?"
  # enabled = true
```

Or as a theme component: clone this repository into `themes/hugo-deskcrew` and add it to `theme = ["your-theme", "hugo-deskcrew"]`.

Then, once, in the base template your pages extend (usually `layouts/_default/baseof.html`), just before `</body>`:

```go-html-template
{{ partial "deskcrew.html" . }}
```

Rebuild the site. The launcher appears on every generated page. Values from `hugo.toml` are validated and escaped; a missing or malformed key renders nothing.

## What the component adds to your site

One script tag loading `https://deskcrew.io/desk.js` with your public widget key. The widget runs inside a Shadow DOM and does not touch your styles. Terms: https://deskcrew.io/terms. Privacy: https://deskcrew.io/privacy.

## License

MIT
