# observations

A tiny personal site for blogs, observations, side quests and things that probably did not need a custom television interface.

The site is deliberately simple: plain HTML, CSS and JavaScript, with a little Firebase behind the editor so new notes can be published without rebuilding the whole thing.

## what is here

- **Blogs** for longer notes
- **Observations** stored as cassette tapes and read on a retro TV
- **About, work, playground and experience** sections
- A browser-based editor for the site content
- Local drafts through `localStorage`
- Firebase publishing for the owner account
- Netlify-ready static hosting

## files

```text
.
├── index.html          # main site
├── Observations.html   # matching standalone copy
├── netlify.toml        # Netlify publish settings
└── README.md           # this note
```

## run it

There is no build step or package install.

Open `index.html` directly in a browser, or serve the folder locally:

```bash
python -m http.server 8000
```

Then open [http://localhost:8000](http://localhost:8000).

## edit the site

Open the site with the `edit` query parameter:

```text
http://localhost:8000/?edit
```

From the editor you can update the profile, blogs, tapes and projects.

- **Save locally** stores a draft in this browser.
- **Download HTML** creates a shareable static copy.
- **Publish online** signs in with Google and writes the content to Firebase.
- **Reset draft** removes the browser-saved draft and restores the original content.

Only the configured owner email is allowed to publish.

## publish with Firebase

The Firebase web configuration lives near the top of the script in both HTML files. Firebase Authentication and Firestore must be configured for the project, and the owner email must match `FIREBASE_ADMIN_EMAIL`.

If the browser blocks the sign-in popup, the editor falls back to redirect authentication and continues publishing when the page returns.

## deploy with Netlify

`netlify.toml` already points Netlify at the current directory:

```toml
[build]
  publish = "."
```

Deploy the folder as a static site. No build command is required.

## small note

`index.html` and `Observations.html` intentionally contain the same site so either file can be used as a standalone copy. Keep their editor logic in sync when making code changes.
