# 🛍️ E-Commerce Catalog

A simple and interactive e-commerce product catalog built using Vue.js. This application fetches product data from the [Fake Store API](https://fakestoreapi.com/) and displays one product at a time. It focuses on showcasing **men's** and **women's clothing**, with the ability to switch between products.

## 🔍 Features

- Dynamic product display using Vue.js.
- Integration with [Fake Store API](https://fakestoreapi.com/).
- Styled display for men's and women's clothing with category-based background.
- Loading indicator while fetching data.
- Responsive design for mobile and desktop.
- Graceful fallback for unsupported product categories.

## 🛠️ Technologies Used

- **Vue.js 3**
- **CSS3**
- **HTML5**
- **Fake Store API**

## 🚀 Getting Started

To run this project locally, follow these steps:

### 1. Clone the repository

```sh
git clone https://github.com/Ilhamgun/ecommerce-catalog.git
```

```sh
cd ecommerce-catalog
```

### 2. Install dependencies
Make sure you have Node.js installed.
```sh
npm install
```

### 3. Run the development server
```sh
npm run dev
```

### 4. Open in browser
Visit http://localhost:5173 in your browser to view the app.

## 💡 How It Works

The app loads a product using its ID from the Fake Store API.

Only products in the categories men's clothing and women's clothing are displayed with full styling.

Products outside of those categories show an "Unavailable" screen.

Users can click "Next product" to cycle through products (1–20).

## 📦 API Reference

Endpoint: https://fakestoreapi.com/products/:id

Example: https://fakestoreapi.com/products/5
