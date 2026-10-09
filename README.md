# The Dog Ronin: static redesign mockup

Files: `index.html`, `styles.css`, `AUDIT.md` (notes on the current live site), `shots/` (render checks). No build step and no dependencies.

Preview locally: open `index.html` in a browser, or run `python3 -m http.server 8000` in this folder and visit http://localhost:8000.

## Placeholders to replace
Search `index.html` for `REPLACE`. Yellow tags on the page mark them too; delete each yellow tag when you fix its item.

| What | Where | Replace with |
|---|---|---|
| Product links (3 cards) | `href="#REPLACE-WITH-..."` in the Shop section | Live TikTok Shop or Amazon product URLs |
| Product names, prices, one-liners, photos | Each `article.prod` | Real listing details and images (`<img>` in place of `.ph`) |
| Buy button label | Each card | "Buy on TikTok Shop" or "Buy on Amazon" to match the link |
| Affiliate disclosure | `.note` under the cards | Wording required by the programs you join |
| TikTok profile link and handle | TikTok section, footer, and `sameAs` in the JSON-LD block | Your profile URL and @handle |
| Other social links | Footer | Instagram, Facebook, X URLs, or delete them |
| Form endpoint | `<form id="inquiry" action=...>` | Your form service URL (see below) |
| Service area, pricing, hours | Walking section and FAQ | Real details |
| `areaServed` | JSON-LD in `<head>` | Your city or area |
| Share image | `og:image` | A real image URL, about 1200x630 |
| Hero and About photos | `.hero-img`, `.portrait` | Real photos (the golden retriever photo on the current site is a good hero) |
| Brand colors | `:root` in `styles.css` | Optional |

Once the listings are live, remove the "Draft mode" banner and the "PLACEHOLDER LINK" tags. Remove the "list these last" remark on the treats card: TikTok Shop treats typically need category qualification.

## Inquiry form
The form is plain HTML with no server code. Until `action` is replaced, the page refuses to submit and shows "not connected yet". Pick one:
- Formspree (or a similar form service): create a form and paste its URL into `action`.
- Your current host's built-in form handler, if it has one. Check its documentation.

The hidden `_gotcha` field is a basic spam trap for Formspree. Test with a real submission before announcing the page.

## Deploying to the existing host
I do not know where thedogronin.com is hosted and have no access to it, so these steps are generic. First find out what the site runs on. The live page loads its form with JavaScript, which suggests a site builder or CMS (for example WordPress), but this is a guess.

1. Back up the current site first (export or backup from the host's dashboard).
2. Replace every placeholder above and open the page locally to check it.
3. Choose the route that fits your host:
   - **Static hosting or cPanel/FTP:** upload `index.html` and `styles.css` to the site's web root (often `public_html`), keeping them in the same folder. This overwrites the existing home page, which is why you back up first. Alternatively upload to a subfolder such as `/new/` and preview at thedogronin.com/new/ before swapping.
   - **Site builder (Wix, Squarespace, Square, GoDaddy and similar):** these do not accept uploaded HTML as a whole site. Use the layout and the copy from this mockup, or paste sections into an embed or custom-code block if the builder offers one.
   - **WordPress:** use the mockup as a design reference, or paste the section markup into custom HTML blocks and move the CSS into Additional CSS.
4. After publishing, check on a phone and on desktop: nav, all buy links, the form submission, and the social links.
5. Submit the URL in Google Search Console if you have it set up, and add the shop link to your TikTok profile bio.

## Verified
Rendered locally in headless Chrome. At 360, 390, 768 and 1280 px the page has no horizontal overflow (scroll width equals viewport width, and no element extends past the edge). Screenshots are in `shots/m390.png`, `shots/m390-full.png` and `shots/d1280.png`. Not tested: real form submission, other browsers, and Lighthouse or accessibility audits.
