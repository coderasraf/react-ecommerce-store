# Comfy Sloth Store

A React e-commerce storefront for a furniture shop, with product filtering, a persistent cart, Auth0 login and a Stripe test checkout handled by a Netlify Function.

![React](https://img.shields.io/badge/React-17-61DAFB?logo=react&logoColor=white)
![Stripe](https://img.shields.io/badge/Stripe-Checkout-635BFF?logo=stripe&logoColor=white)
![Auth0](https://img.shields.io/badge/Auth0-Login-EB5424?logo=auth0&logoColor=white)
![Netlify](https://img.shields.io/badge/Netlify-Functions-00C7B7?logo=netlify&logoColor=white)

## About

Built in 2022 as a learning project following John Smilga's "Comfy Sloth" e-commerce project. It focuses on managing app-wide state with the Context API and `useReducer`, integrating third-party auth and payments, and running a serverless function on Netlify. Product data comes from the course's public API (`course-api.com`).

## Features

- Home page with hero, featured products, services and contact sections
- Products page with:
  - Search by name
  - Filters for category, company, color, max price and free shipping
  - Sort by price (low/high) and name (A-Z / Z-A)
  - Grid and list views
- Single product page with image gallery, star rating, stock info, color selection and quantity picker
- Cart with quantity controls, item removal, clear cart, subtotal, shipping fee and order total
- Cart saved to `localStorage`
- Auth0 login/logout; checkout route protected for signed-in users
- Stripe card payment using `CardElement` and a PaymentIntent created by a Netlify Function
- Responsive navbar and sidebar, 404 page

## Tech Stack

- React 17 (Create React App)
- React Router v6
- Context API + `useReducer`
- styled-components, React Icons
- Auth0 (`@auth0/auth0-react`)
- Stripe (`@stripe/react-stripe-js`, `@stripe/stripe-js`, `stripe`)
- Netlify Functions, Netlify CLI
- axios

## Getting Started

Prerequisites: Node.js, npm, an Auth0 SPA application and a Stripe account (test keys).

```bash
git clone https://github.com/coderasraf/react-ecommerce-store.git
cd react-ecommerce-store
npm install
```

Create a `.env` file (see below), then:

```bash
npm run dev      # netlify dev: React app + serverless functions
npm start        # React app only (checkout will not work)
npm run build    # production build
```

In your Auth0 application settings, add your local and deployed URLs (for example `http://localhost:8888` when using `netlify dev`) to Allowed Callback URLs, Allowed Logout URLs and Allowed Web Origins.

## Environment Variables

| Name | Purpose |
| --- | --- |
| `REACT_APP_AUTH_DOMAIN` | Auth0 domain |
| `REACT_APP_CLIENT_ID` | Auth0 client ID |
| `REACT_APP_STRIPE_PUBLIC_KEY` | Stripe publishable key (client) |
| `REACT_APP_STRIPE_SECRET_KEY` | Stripe secret key (used only by the Netlify Function) |

## Project Structure

```text
├── functions/
│   └── create-payment-intent.js   # Stripe PaymentIntent (Netlify Function)
├── netlify.toml
├── public/_redirects              # SPA routing on Netlify
└── src/
    ├── App.js                     # Routes
    ├── components/                # Navbar, Filters, Sort, CartItem, StripeCheckout, ...
    ├── context/                   # products, filter, cart, user contexts
    ├── reducers/                  # products, filter, cart reducers
    ├── pages/                     # Home, Products, SingleProduct, Cart, Checkout, About
    └── utils/                     # constants (API URLs), helpers
```

## Author

Built by **Ashraf Siddik**, Shopify developer & CRO specialist.
- Website: [ashraf-siddik.com](https://ashraf-siddik.com)
- GitHub: [@coderasraf](https://github.com/coderasraf)
