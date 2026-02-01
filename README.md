# Price Tracker

This is a Next.js application that allows users to track prices of products from e-commerce websites. It scrapes the product page, stores the price history, and notifies the user when the price drops.

## Features

*   **User Authentication:** Secure user authentication using Supabase.
*   **Add Products:** Add products to track by providing the product page URL.
*   **Price History:** View the price history of a product in a chart.
*   **Automated Price Checking:** A cron job runs periodically to check for price changes.
*   **Email Notifications:** Receive email notifications when a product's price drops.
*   **Web Scraping:** Uses Firecrawl to scrape product information from any website.

## Tech Stack

*   **Framework:** [Next.js](https://nextjs.org/)
*   **Authentication:** [Supabase](https://supabase.io/)
*   **Database:** [Supabase Postgres](https://supabase.io/database)
*   **Scraping:** [Firecrawl](https://firecrawl.dev/)
*   **Email:** [Resend](https://resend.com/)
*   **UI:** [Shadcn/ui](https://ui.shadcn.com/)
*   **Charting:** [Recharts](https://recharts.org/)
*   **Styling:** [Tailwind CSS](https://tailwindcss.com/)

## Getting Started

### Prerequisites

*   Node.js (v20 or later)
*   npm

### Installation

1.  Clone the repository:
    ```bash
    git clone https://github.com/your-username/price-tracker.git
    cd price-tracker/my-app
    ```
2.  Install dependencies:
    ```bash
    npm install
    ```
3.  Set up environment variables. Create a `.env.local` file in the `my-app` directory and add the following:
    ```
    NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
    NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
    SUPABASE_SERVICE_ROLE_KEY=your_supabase_service_role_key
    RESEND_API_KEY=your_resend_api_key
    FIRECRAWL_API_KEY=your_firecrawl_api_key
    ```
4.  Set up the database schema in Supabase. You'll need tables for `users` and `products`.

### Running the Application

1.  Run the development server:
    ```bash
    npm run dev
    ```
2.  Open [http://localhost:3000](http://localhost:3000) in your browser.

## How It Works

1.  **Add Product:** A user pastes a product URL into the form.
2.  **Scraping:** Firecrawl is used to scrape the product title, price, and image from the URL.
3.  **Database:** The product information is saved to the Supabase database.
4.  **Cron Job:** A cron job is set up to run periodically. It iterates through the products in the database and re-scrapes the pages to get the current price.
5.  **Price Check:** If the price has changed, the new price is added to a price history array in the database.
6.  **Email Notification:** If the price has dropped, an email is sent to the user who added the product, notifying them of the price drop.
