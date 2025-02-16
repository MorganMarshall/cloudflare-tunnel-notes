# Cloudflare tunnel notes

### How to Secure New Cloudflare Tunnel Endpoints?

To prevent exposure, apply these protections:
- Restrict Access with Cloudflare Access (Best Method)
Go to Cloudflare Dashboard → Zero Trust → Access → Applications
Add a new application (Self-hosted)
Restrict access to authenticated users (via Google, GitHub, SSO, etc.)

- Lock Down with Cloudflare Firewall Rules
Go to Cloudflare Dashboard → Security → WAF → Firewall Rules
Create a rule:
If URL Path contains /your-tunnel-endpoint
AND Country is NOT your country (Optional)
Then Block

- Require Token Authentication
If your app supports Bearer Tokens or API Keys, enforce it:
Modify your backend application to check for:
Authorization: Bearer YOUR_SECRET_TOKEN
If missing, reject the request with HTTP 403

