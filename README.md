# Cole's Big Playground

The game lives in `index.html`. Everything it needs is inside that one file, so
once the page has been opened once it works with no internet.

The grown-up guide is at `parent-guide.html`, which is `yoursite/parent-guide.html`
once this is published.

## Publishing it (once)

1. On github.com, click **+** at the top right, then **New repository**.
2. Name it `coles-playground`, choose **Public**, and click **Create repository**.
3. On the new repository page, click **uploading an existing file**.
4. Drag in every file from this folder, then click **Commit changes**.
5. Click **Settings**, then **Pages** in the left sidebar.
6. Under **Branch**, choose `main` and folder `/ (root)`, then **Save**.
7. Wait a minute, refresh, and the address appears at the top of that page:
   `https://YOURNAME.github.io/coles-playground`

## Putting it on the iPad

1. Open that address in **Safari**.
2. Tap the **share button**: the square with an arrow pointing up, top right.
3. Scroll down, tap **Add to Home Screen**, then **Add**.

It gets its own icon, opens full screen, and works without wifi from then on.

A local `.html` file will not work this way. iOS opens it in a preview that cannot
run the game, which is why it needs publishing first.

## Putting a new build up later

1. In the repository, click on `index.html`, then the pencil icon.
2. Delete everything and paste in the new build. Or simpler: from the repository
   home, **Add file → Upload files**, drag the new `index.html` in, and commit.
   It replaces the old one.
3. Also replace `sw.js` if the new build came with one; its cache name changes
   each build, which is what makes the iPad pick up the new version.
4. On the iPad, close the app fully and reopen it twice.

The tiny text in the bottom right corner of the opening screen shows which build
is running.

## What each file is

| File | What it does |
| --- | --- |
| `index.html` | The whole game |
| `parent-guide.html` | The grown-up guide as its own page |
| `sw.js` | Makes the game work offline |
| `manifest.webmanifest` | Name and icon for the home screen |
| `icon-192.png`, `icon-512.png`, `apple-touch-icon.png` | The home screen icons |
