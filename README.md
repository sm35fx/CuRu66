# 6N Copper — multilingual B2B landing (production-ready starter)

Premium responsive static website for a high-purity copper / precision-metals exporter. Built from the supplied technical specification and the visual direction of the provided DISF reference sites.

## Included
- RU / EN / DE / 中文 switching without page reload.
- Desktop / tablet / mobile layout.
- Sticky header, mobile menu, floating quotation CTA.
- Product tabs: copper, aluminium, rare earths, gold.
- Product modal with specifications.
- Quality / GDMS / SDS block.
- Process and international logistics section.
- FAQ and quotation form.
- Privacy / Terms / Thank-you pages.
- SEO title/description, Open Graph, robots.txt, sitemap.xml, web manifest.
- Basic security headers for Cloudflare Pages.
- Optional Cloudflare Turnstile.
- Optional Cloudflare Web Analytics.
- Free email delivery via FormSubmit can be enabled in `config.js`.
- Open-license / public-domain image analogs; no client photo upload is required for the design.

## Images
The website intentionally uses illustrative analogs from open-license sources instead of pretending they are the seller's own product photographs.

Verified sources include:
- Copper ingot — Wikimedia Commons, CC0/public domain: https://commons.wikimedia.org/wiki/File:Copper_ingot,_Democratic_Republic_of_the_Congo,_collected_before_1914_-_Royal_Ontario_Museum_-_DSC09597.JPG
- Copper powder — Wikimedia Commons, CC BY-SA 4.0: https://commons.wikimedia.org/wiki/File:Atomized_copper_powder.jpg
- Gold bullion — Wikimedia Commons, CC0: https://commons.wikimedia.org/wiki/File:Gold_bullion_bars.jpg
- Other industrial/reference imagery is linked in the site's image-reference note.

For a final commercial launch, replace illustrative images with licensed product-specific photography if available.

## 1. Configure the company
Open `config.js` and replace:

- `siteUrl`
- `companyName`
- `salesEmail`
- `formSubmitEmail`
- `whatsapp`
- `telegram`
- `wechat`

Example:

```js
window.SITE_CONFIG = {
  siteUrl: 'https://example.com',
  companyName: 'Example Metals',
  salesEmail: 'sales@example.com',
  whatsapp: '971501234567',
  telegram: 'https://t.me/example',
  wechat: '',
  formSubmitEmail: 'sales@example.com',
  turnstileSiteKey: '',
  analyticsToken: ''
};
```

`whatsapp` should contain the international phone number without `+`, spaces or brackets.

## 2. Free quotation email
The current project supports FormSubmit's AJAX endpoint. FormSubmit states that its basic form backend is free and requires no PHP/Node backend; the first submission activates the recipient address by confirmation email.

Set `formSubmitEmail` to the mailbox that should receive enquiries. Submit one test request after deployment and confirm the activation email.

For higher-control production deployments, replace FormSubmit with a Cloudflare Worker / Pages Function and your preferred transactional email provider.

## 3. Anti-spam
A honeypot is included. FormSubmit can also display its captcha protection. For stronger Cloudflare-native protection, create a Turnstile widget and put its public site key in `config.js` as `turnstileSiteKey`.

The secret key must NEVER be put in `config.js`; it belongs in a server-side Worker/Pages Function.

## 4. Cloudflare Pages deployment — recommended
Cloudflare Pages supports static HTML directly.

### GitHub method
1. Create a GitHub repository, for example `6n-copper-site`.
2. Upload the contents of this folder (not the outer ZIP folder itself).
3. In Cloudflare Dashboard open **Workers & Pages → Create application → Pages → Import an existing Git repository**.
4. Select the repository.
5. Production branch: `main`.
6. Framework preset: none.
7. Build command: `exit 0`.
8. Build output directory: `.`
9. Deploy.
10. Cloudflare will provide a `*.pages.dev` address.

### Custom domain
Open the Pages project → **Custom domains → Set up a domain** and enter your domain. For an apex domain, Cloudflare requires the domain to be a zone on the same Cloudflare account; for a subdomain, a CNAME can point to the Pages address.

## 5. Cloudflare Web Analytics
The site has an optional `analyticsToken` field. Alternatively, Pages provides one-click Web Analytics from the project Metrics section. This is preferable to adding a large third-party analytics stack.

If using the token field, paste the site token supplied by Cloudflare Web Analytics. Do not paste API tokens or account secrets into the website.

## 6. Domain / SEO
After the real domain is known:
- replace `YOUR-DOMAIN.example` in `robots.txt` and `sitemap.xml`;
- update `config.js`;
- update the Open Graph URL if a production image is later added;
- submit `https://YOUR-DOMAIN/sitemap.xml` in Google Search Console and Bing Webmaster Tools.

## 7. Certificates
Put real PDFs in `data/certificates/` and add links in the Quality section. Do not publish sample or placeholder certificates as genuine company documents.

## 8. Contact channels
WhatsApp / Telegram / WeChat are hidden automatically when their values are blank. Add the real public contact identifiers in `config.js`.

## 9. Local test
No Node.js build is required:

```bash
python3 -m http.server 8080
```

Open `http://localhost:8080`.

## 10. Production checklist
Before advertising the site:
- Replace placeholder company name and email.
- Configure the form recipient and submit a real test.
- Add real certificates / SDS / GDMS files.
- Verify product specifications and MOQ against the commercial offer.
- Add actual WhatsApp / Telegram / WeChat links.
- Configure Cloudflare Turnstile if needed.
- Enable Cloudflare Web Analytics.
- Replace `YOUR-DOMAIN.example` in robots/sitemap.
- Replace generic privacy/terms text with company-approved legal text.
- Confirm image licenses and keep the source/credit note in the project archive.

## Sources checked
Cloudflare Pages supports static HTML deployments and GitHub/GitLab integration. Cloudflare Pages provides a `*.pages.dev` address after deployment and supports custom domains. Cloudflare Turnstile is available on the Free plan, and Cloudflare Web Analytics is available as a privacy-first free analytics option. FormSubmit provides a free HTML form endpoint and AJAX submission option.

## v4 visual upgrade
The v4 interface adds a premium editorial / advanced-materials presentation: oversized typography, cinematic image panels, copper-accent micro-details, application cards, stronger product cards, analytical-control section, logistics visual, reveal-on-scroll motion and improved mobile composition. The site remains static HTML/CSS/JS and deployable on Cloudflare Pages.
