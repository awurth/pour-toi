# pour-toi

A single-page gift reveal: open the link, tap the button, the gift appears. Static files, no dependency, no external request.

## Edit the gift

Every text lives in the `GIFT` object at the top of the `<script>` in `index.html`:

| Key | Shown as |
|---|---|
| `greeting` | the title of the opening screen |
| `kind` | the line above the concert name |
| `concert` | the big title of the reveal |
| `tagline` | the line under the concert name |
| `note` | the personal line under the title |
| `venue`, `date` | the details below it |

Two files repeat part of it and must be updated by hand when the event changes:

- `rendez-vous.ics`: the calendar event behind the "Ajouter au calendrier" button (times in UTC).
- `preview.jpg`: the image shown in link previews (WhatsApp, iMessage…), a 1200×630 capture of the opening screen. Its absolute URL is in the `og:image` meta tag: update it if the repository is renamed.

## Link

The page only shows up when the URL carries the token set in `ACCESS_TOKEN`: `index.html?t=<token>`. Without it, visitors get a neutral "link is incomplete" message. This only keeps casual visitors out: the content stays readable in the source.

To check the page locally, open `index.html?t=<token>` in a browser.

## Publish on GitHub Pages

1. Create a repository with a neutral name (e.g. `pour-toi`): it shows in the URL.
2. Push this repository to it:
   ```bash
   git remote add origin git@github.com:<user>/<repo>.git
   git push -u origin main
   ```
3. In the repository: **Settings › Pages**, source *Deploy from a branch*, branch `main`, folder `/ (root)`, **Save**.
4. After a minute or two the page is live at `https://<user>.github.io/<repo>/`.

On a free GitHub plan, Pages needs a public repository: anyone browsing your profile can read the gift in the source. `noindex` keeps the page out of search engines only.
