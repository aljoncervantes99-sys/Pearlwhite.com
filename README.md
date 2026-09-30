# Pearl White — Website Source

A single-page, fully static vacation-rental website. No build step, no
framework, no backend — plain HTML, CSS and JavaScript.

## Files

```
index.html              The whole site (all sections, one page)
assets/css/style.css     All styles (colors, layout, animations)
assets/js/script.js      All behavior (gallery, booking form, availability check)
assets/images/           Empty — see assets/images/README.md to add real photos
netlify.toml             Netlify deploy config (optional)
vercel.json              Vercel deploy config (optional)
package.json             Only used to run a local preview server
```

## Run it locally

You don't need Node.js or any build tool — you can just double-click
`index.html` to open it in a browser. For a closer-to-production preview
(recommended, since some browsers restrict local file access):

```bash
npx http-server . -p 8080
# then open http://localhost:8080
```

or, if you have Node installed:

```bash
npm start
```

## Deploy it

Any static host works. A few easy options:

- **Netlify / Vercel**: drag the whole folder into their dashboard, or connect
  a GitHub repo — both platforms auto-detect a static site with no config
  needed (the included `netlify.toml` / `vercel.json` are optional extras).
- **GitHub Pages**: push this folder to a repo and enable Pages on the `main`
  branch.
- **Any web host / cPanel / FTP**: upload the whole folder to your `public_html`
  (or equivalent) directory as-is.

## Things to edit before going live

1. **Photos** — see `assets/images/README.md`. Every image is currently a
   placeholder tile.
2. **Booking notifications** — open `assets/js/script.js` and find:
   ```js
   const HOST_EMAIL="aljoncervantes99@gmail.com";
   const HOST_WHATSAPP="639518232858";
   ```
   These are already set. Change them if you want requests sent elsewhere.
3. **Location details** — currently filled in for Pasay, Manila
   (`index.html`, "Everything Within Reach" section). Update if the property
   is elsewhere.
4. **Room names, prices, capacity** — in `assets/js/script.js`, the `stays`
   array near the top.
5. **House rules, cancellation policy, reviews** — search `index.html` for
   `[Policy]` and `[ADD` placeholders and replace with your real text.
6. **Availability / blocked dates** — in `assets/js/script.js`, the `blocked`
   array is a hardcoded example. For real-time availability synced to a
   calendar or booking platform (Airbnb, Booking.com, etc.), you'll need a
   small backend or a booking-platform integration — this static version
   checks against the dates you list manually.

## How booking requests work

There's no backend. When a guest submits the booking form after checking
availability, the page opens either:

- a pre-filled **WhatsApp** message to your number, or
- a pre-filled **email** to your address

The guest still has to hit send in their own app — a static site can't send
messages on its own. If you later want fully automatic notifications with no
guest action required, that needs a real backend or a form service (e.g.
Formspree, Netlify Forms, Zapier) or the WhatsApp Business API.
