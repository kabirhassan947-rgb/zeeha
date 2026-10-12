# Zeeha website

Abayas and modest wear store. Plain HTML, CSS and JavaScript, so it hosts free on GitHub Pages.

## Publish on GitHub

1. Create a free account at github.com and click **New repository**. Name it `zeeha` and set it to **Public**.
2. Click **uploading an existing file**, drag in everything from this folder (`index.html`, `admin.html`, `products.json`, `README.md`, and `logo.png`), then click **Commit changes**.
3. Go to **Settings > Pages**. Under **Branch**, choose `main` and `/ (root)`, then **Save**.
4. After about a minute your shop is live at `https://YOUR-USERNAME.github.io/zeeha/`.
5. Want `zeeha.com.ng` or similar? Buy the domain, then add it under **Settings > Pages > Custom domain**.

## Before you go live

Open `admin.html` (at `your-site/admin.html`) and set:

- **WhatsApp number**: format `2348012345678`.
- **Paystack public key**: create a Paystack account (paystack.com), complete business verification, and paste your **public** key (`pk_live_...`). Customers can then pay by card, bank transfer and USSD. Never paste your secret key anywhere.
- **Delivery fees and times**, then **Email**.

Click **Download products.json** and upload it to the repository, replacing the old one.

## Adding products and photos

1. Upload photos to the main list on GitHub (**Add file > Upload files**). Use small files, around 1000px wide and under 300 KB each.
2. In `admin.html`, click **+ New product** and fill in the details. For photos write the path, for example `noor-1.jpg`.
3. Download `products.json` and upload it to GitHub. Stock, prices and sold-out labels all come from this file.

## Good to know

- After each order, check your Paystack dashboard for the payment and customer details, then reduce stock in `admin.html`.
- Prices are set in the browser, so always confirm the amount paid in Paystack matches the order before shipping.
- To preview on your computer, run `python3 -m http.server` in this folder and open `http://localhost:8000`. Opening `index.html` directly will not load the products.
