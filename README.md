<!-- deskcrew-header:start -->
<p align="center">
  <a href="https://deskcrew.io"><img src="https://deskcrew.io/logo.png" alt="DeskCrew" width="96" height="96"></a>
</p>

<h1 align="center">hugo-deskcrew</h1>

<p align="center"><b>Hugo theme component that adds the DeskCrew support widget to every page</b></p>

<p align="center">AI live chat, tickets and a help center from one partial and a params block.</p>

<p align="center">
  <a href="https://deskcrew.io"><b>Website</b></a> •
  <a href="https://deskcrew.io/integrations"><b>Integrations</b></a> •
  <a href="https://deskcrew.io/agents"><b>For agents</b></a> •
  <a href="https://deskcrew.io/signup"><b>Sign up</b></a>
</p>

<p align="center">
  <a href="https://github.com/webmilmind1/hugo-deskcrew/stargazers"><img src="https://img.shields.io/github/stars/webmilmind1/hugo-deskcrew?style=flat&logo=github&label=Stars&color=ffd33d" alt="GitHub stars"></a>
  <a href="https://github.com/webmilmind1/hugo-deskcrew"><img src="https://img.shields.io/github/license/webmilmind1/hugo-deskcrew?style=flat&label=License&color=e3a82b" alt="License"></a>
</p>

<p align="center">
  <a href="https://deskcrew.io"><img src="https://img.shields.io/badge/Visit_our_website-6366F1?style=for-the-badge&logoColor=white" alt="Visit our website"></a>
  <a href="https://discord.gg/hdWZgrYDqB"><img src="https://img.shields.io/badge/Join_our_Discord-5865F2?style=for-the-badge&logoColor=white&logo=discord" alt="Join our Discord"></a>
  <a href="https://x.com/getdeskcrew"><img src="https://img.shields.io/badge/Follow_%40getdeskcrew-000000?style=for-the-badge&logoColor=white&logo=x" alt="Follow @getdeskcrew"></a>
  <a href="https://www.instagram.com/getdeskcrew"><img src="https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logoColor=white&logo=instagram" alt="Instagram"></a>
  <a href="https://mastodon.social/@deskcrew"><img src="https://img.shields.io/badge/Mastodon-6364FF?style=for-the-badge&logoColor=white&logo=mastodon" alt="Mastodon"></a>
  <a href="https://www.youtube.com/channel/UCW7g7TLiUbnK8zWF513ckFA"><img src="https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logoColor=white&logo=youtube" alt="YouTube"></a>
  <a href="https://www.tiktok.com/@deskcrewhq"><img src="https://img.shields.io/badge/TikTok-000000?style=for-the-badge&logoColor=white&logo=tiktok" alt="TikTok"></a>
</p>

<p align="center"><i>⭐ Help more people find DeskCrew. Star this repo!</i></p>
<!-- deskcrew-header:end -->

![DeskCrew widget for Hugo](https://deskcrew.io/packages/deskcrew-hugo.gif)

**Live chat, an AI support chatbot and a help center for Hugo, from one partial and a few lines in `hugo.toml`.** hugo-deskcrew is a theme component that adds the [DeskCrew](https://deskcrew.io) support widget to every page of a Hugo site: visitors chat with an AI that answers from your knowledge base, anything it cannot answer becomes a ticket, and a human approves every reply before it sends. It sits alongside your existing theme, so nothing in it changes.

Works with PaperMod, Docsy, Hextra, Book, Ananke, Blowfish and any other theme, as a Hugo module or a theme component, on Netlify, Cloudflare Pages, Vercel and GitHub Pages. Free plan, no credit card: https://deskcrew.io/signup

## Use it for

- **Live chat on a Hugo blog or documentation site** without editing the theme's templates.
- **An AI chatbot for docs**: it answers from the help articles you publish and hands off to a person when it is unsure.
- **A contact form replacement**: visitors ask in the widget, you get a ticket, no form backend or serverless function to host.
- **A help center for a static product or SaaS marketing site** that stays on your domain.

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

## FAQ

### How do I add live chat to a Hugo site?

Import this component as a Hugo module (or clone it into `themes/`), put your widget key under `[params.deskcrew]` in `hugo.toml`, and call `{{ partial "deskcrew.html" . }}` once before `</body>` in your base template. Every page gets the chat bubble on the next build.

### Does it work with PaperMod, Docsy, Hextra or Book?

Yes. It is a theme component, not a theme, so it stacks on top of whatever theme you run. If your theme already exposes a hook for extra body content (PaperMod's `extend_footer.html`, Docsy's `hooks/body-end.html`, Hextra's `custom/body-end.html`), put the partial call there and you never touch `baseof.html`.

### Does it work on GitHub Pages?

Yes. The output is one script tag in your generated HTML, so any host that serves the built site works, including GitHub Pages built with a GitHub Actions workflow, Netlify, Cloudflare Pages and Vercel.

### Does it change my theme or styles?

No. The partial renders a single script tag, and the widget runs inside a Shadow DOM so your CSS and its CSS never collide. Remove the partial call and the site is exactly as before.

### Can I turn it off in development or on some pages?

Set `enabled = false` under `[params.deskcrew]` in a development config (for example `config/development/hugo.toml`) to keep the component installed with the widget off. To skip specific pages, wrap the partial call in a condition on the page's front matter.

### Is the AI chatbot going to make things up?

It answers only from the knowledge base you publish on DeskCrew and says so when it does not know. Anything it cannot answer becomes a ticket, and a person approves every outbound reply.

### Is there a free plan?

Yes. The component is MIT and the DeskCrew free plan includes the chat widget, ticketing, a public help center and a monthly AI answer allowance, with no credit card.

### Which Hugo versions are supported?

Hugo 0.110 and newer, standard or extended build.

## What the component adds to your site

One script tag loading `https://deskcrew.io/desk.js` with your public widget key. The widget runs inside a Shadow DOM and does not touch your styles. Terms: https://deskcrew.io/terms. Privacy: https://deskcrew.io/privacy.

## License

MIT
