# Sillage Club — Stripe Checkout Ready

This package contains:
- `index.html` — Sillage Club storefront/landing page
- `images/` — the five product images
- `api/create-checkout-session.js` — server-side Stripe Checkout endpoint
- `success.html` — branded post-checkout page

## Stripe setup

Create the five products/prices in Stripe Sandbox, then create:
- U.S. shipping rate: $4
- International shipping rate: $10

Add these environment variables to the deployment:

STRIPE_SECRET_KEY=your_test_secret_key
STRIPE_PRICE_DIOR=price_...
STRIPE_PRICE_LIBRE=price_...
STRIPE_PRICE_JPG=price_...
STRIPE_PRICE_LAYTON=price_...
STRIPE_PRICE_AVENTUS=price_...
STRIPE_SHIPPING_US=shr_...
STRIPE_SHIPPING_INTL=shr_...
SITE_URL=https://your-domain.com

Install the Stripe Node package:
npm install stripe

## Important Arizona note

Stripe Checkout does not natively make a shipping rate appear only when the address is in Arizona. The storefront currently displays Arizona local delivery as an option, but the included server endpoint deliberately blocks it until address validation is added. Do not enable Arizona local checkout until that validation step is implemented.

## Deployment

The API file is written in a Vercel-style serverless format (`/api/create-checkout-session.js`). A Vercel deployment can host the static page and API together. Keep `STRIPE_SECRET_KEY` server-side only.

The product images and prices shown on the page are the current Sillage Club lineup:
Dior Sauvage EDP 100ml $119.99
YSL Libre EDP 90ml $129.99
JPG Le Male Elixir 125ml $129.99
Parfums de Marly Layton 125ml $279.99
Creed Aventus 100ml $349.99
