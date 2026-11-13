# pour-toi

A single-page gift reveal: open the link, tap the button, the gift appears. One `index.html`, no dependency, no external request.

## Edit the gift

Every text lives in the `GIFT` object at the top of the `<script>` in `index.html`:

| Key | Shown as |
|---|---|
| `greeting` | the title of the opening screen |
| `kind` | the line above the concert name |
| `concert` | the big title of the reveal |
| `tagline` | the line under the concert name |
| `venue`, `date`, `category` | the details below it |

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
