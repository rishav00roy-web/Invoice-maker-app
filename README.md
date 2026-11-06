# Invoice Reader

An AI invoice and receipt reader for small businesses, by [Atelier Systems](https://byrishav.online).

Upload a photo of a receipt or a PDF invoice. The AI reads it and fills in the date, vendor, amounts, tax and line items, puts it in the right category, converts the currency, and saves it to a searchable table you can export to CSV for your accountant.

## What it does

- **Reads any bill.** Store receipts, restaurant bills, GST invoices, bank statements, even handwritten slips, in any language.
- **Sorts it for you.** Automatic categories and projects, plus your own custom fields and prompts.
- **Handles currencies.** Converts to your base currency using the rate on the bill's date.
- **Exports cleanly.** Filtered CSV exports with the original documents attached.
- **Stays private.** Runs on your own server with your own database. Your documents never leave it.

Works with Google Gemini, OpenAI, Mistral, or any OpenAI-compatible endpoint. A free Gemini key is the easiest start.

## Run it

You need [Docker](https://www.docker.com/products/docker-desktop/).

```bash
git clone https://github.com/rishav00roy-web/invoice-maker-app.git
cd invoice-maker-app
docker compose up --build
```

Open http://localhost:7331 and add your AI key in Settings.

> This edition has no login by default (`SELF_HOSTED_MODE=true`). Keep it on your own machine or behind a password. Don't expose it to the open internet as-is.

### Settings

| Variable | What it's for |
|---|---|
| `DATABASE_URL` | Postgres connection (set for you in `docker-compose.yml`) |
| `UPLOAD_PATH` | Where uploaded files are stored |
| `GOOGLE_API_KEY` / `OPENAI_API_KEY` / `MISTRAL_API_KEY` | Your AI provider key (can also be set in the app) |
| `SUPPORT_EMAIL` | Optional contact email shown in the app |
| `DISABLE_SIGNUP` | Set `true` to stop new sign-ups |

For local development: `npm install`, copy `.env.example` to `.env`, run `npx prisma migrate dev`, then `npm run dev`.

## Credits

Built on [TaxHacker](https://github.com/vas3k/TaxHacker) by Vasily Zubarev (vas3k), released under the MIT License. This copy is based on TaxHacker v0.8.5. The original license is kept in [LICENSE](LICENSE).
