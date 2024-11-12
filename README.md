# Daraz Product Scraper and Sentiment Analysis

This project is a web scraper and sentiment analysis tool designed to help users find the best available Redmi Note 12 smartphone on Daraz. It scrapes product information, applies a custom scoring system to determine the best product, and then performs sentiment analysis on the product reviews using NLTK.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Data Fields](#data-fields)
- [Scoring Criteria](#scoring-criteria)
- [Example Output](#example-output)
- [Disclaimer](#disclaimer)
- [Contributing](#contributing)
- [License](#license)

## Features

- Scrapes information about Redmi Note 12 listings on the first five pages of Daraz.
- Collects essential product details such as title, price, rating, free shipping status, Daraz Mall status, seller rating, and ship-on-time score.
- Calculates a custom score for each product to determine the best option.
- Scrapes reviews of the best product and performs sentiment analysis using NLTK’s SentimentIntensityAnalyzer.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/Hasnain2430/Daraz-RedmiNote12-Scraper.git
   ```

2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Download and set up [ChromeDriver](https://sites.google.com/a/chromium.org/chromedriver/downloads) (or use WebDriver Manager for automated setup).

## Usage

1. Open the main script (`daraz_scraper.py`) in a Jupyter Notebook or similar environment.
2. Run each cell in sequence to start scraping product details and perform the sentiment analysis.
3. The script will:
   - Search for Redmi Note 12 on Daraz and scrape relevant product information from the first five pages.
   - Calculate a custom score for each product based on defined criteria and select the best option.
   - Open the product page for the best-scored product, scrape its reviews, and perform sentiment analysis on the reviews.

4. The results will be saved in two separate DataFrames:
   - `Daraz_Data.csv`: Contains the product data with calculated scores.
   - `reviewss.csv`: Contains the review text, sentiment classification (positive, neutral, or negative), and polarity scores.

## Data Fields

The tool collects the following data fields for each product:

- **Product Title**: Name of the product.
- **Price**: Price of the product (base score).
- **Rating**: Product rating.
- **Free Shipping Status**: Whether free shipping is available.
- **Daraz Mall Status**: Whether the product is listed under Daraz Mall.
- **Seller Rating**: Seller’s rating percentage.
- **Ship on Time Score**: Seller’s shipping performance percentage.
- **Link**: Direct link to the product listing.

## Scoring Criteria

Each product's score is calculated based on the following criteria:

1. The **price** is the base score.
2. **Daraz Mall** status adds 5,000 points.
3. **Free Shipping** status adds 1,000 points.
4. A custom formula based on product rating, seller rating, and shipping performance:
   ```
   10000 * ((0.4 * (Product Rating / 5)) + (0.4 * (Seller Rating / 100)) + (0.2 * (Shipping Performance / 100)))
   ```

The product with the highest score is selected as the best available product.

## Example Output

The output is saved in CSV format and can be imported into any data analysis tool for further processing. The best product's reviews are classified as positive, neutral, or negative, with polarity scores displayed for deeper insights.

## Disclaimer

The scraper may not work properly or may require adjustments if the HTML structure of Daraz's website has changed. Please inspect the page structure and update the XPath or CSS selectors as necessary.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request to improve the project.

