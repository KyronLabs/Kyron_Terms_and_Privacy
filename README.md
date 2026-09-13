# Kyron terms and privacy

The two legal pages the app links out to, served as static HTML from
`https://kyron-terms-and-privacy.onrender.com`.

| | |
|:--|:--|
| `terms.html` | Terms of Service, plain-English edition |
| `privacy.html` | Privacy Policy, full edition |
| `logo.svg` | Kyron's mark — the same file the app draws, copied from `app/lib/assets/logo.svg` in [KyronLabs/kyron](https://github.com/KyronLabs/kyron) |

The app's links to these live in
[`app/lib/config/legal_links.dart`](https://github.com/KyronLabs/kyron/blob/main/app/lib/config/legal_links.dart),
and the get-started screen will not let anybody past until they have been
shown. Changing a filename here breaks that, so don't.

## Two things to know before editing

**The pages are gated.** `<main>` starts `hidden` and an age prompt runs
first — at least 13, for COPPA. Anything added outside `#mainContent` is
visible before somebody has answered it.

**Tailwind is the play CDN**, `cdn.tailwindcss.com`, which compiles the CSS in
the reader's browser. Tailwind's own documentation says not to use it in
production, and it means these pages are unstyled for as long as that script
takes to arrive — on a legal page somebody was sent to from an app. Worth
replacing with a built stylesheet.
