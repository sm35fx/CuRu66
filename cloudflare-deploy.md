# Cloudflare Pages — 10 minute deployment

1. Create a GitHub account/repository.
2. Upload the **contents** of this project folder to the repository.
3. Open Cloudflare Dashboard.
4. Go to **Workers & Pages** → **Create application** → **Pages** → **Import an existing Git repository**.
5. Select your GitHub repository.
6. Use:
   - Production branch: `main`
   - Framework preset: `None`
   - Build command: `exit 0`
   - Build output directory: `.`
7. Click **Save and Deploy**.
8. Open the generated `https://PROJECT.pages.dev` address.
9. In `config.js`, set your company email and form recipient, then commit the change. Cloudflare will automatically redeploy from GitHub.
10. Add your domain under **Pages → Custom domains**.

## Recommended Cloudflare settings
- Enable HTTPS / SSL.
- Enable Web Analytics from **Metrics**.
- Enable Bot Fight Mode where appropriate.
- Create a Turnstile widget for the quotation form if stronger anti-bot protection is required.

## Form
The starter project uses FormSubmit for a zero-server email route. Set `formSubmitEmail` in `config.js`, deploy, submit one test request, and confirm the activation email.

For a more controlled enterprise setup, replace FormSubmit with a Pages Function / Worker and a transactional email provider. Keep Turnstile's secret key server-side.
