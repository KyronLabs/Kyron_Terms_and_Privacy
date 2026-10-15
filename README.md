# Kyron terms and privacy

The two legal pages the app links out to, served as static HTML from
`https://kyron-terms-and-privacy.onrender.com`.

| | |
|:--|:--|
| `terms.html` | Terms of Service, plain-English edition |
| `privacy.html` | Privacy Policy, full edition |
| `delete-account.html` | How to delete an account, in the app or by email. The URL Google Play's Data safety form asks for, so it is not age-gated: somebody leaving, or a parent, has to be able to read it |
| `child-safety.html` | Kyron's standards against child sexual abuse and exploitation: what is not allowed, how to report it, and what is done with a report. The URL Google Play's child safety standards declaration asks for, so it is not age-gated either |
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
