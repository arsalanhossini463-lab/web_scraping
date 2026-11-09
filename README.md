# Technolife Laptop Scraper

A Python script that scrapes laptop listings from the online store [Technolife](https://www.technolife.com), saves them in a SQLite database, and shows them in a simple web page built with Streamlit.

## Features

- Scrapes the description, price, image and link of each laptop with `requests` and BeautifulSoup
- Saves the data in a local SQLite database (`LaptopData.db`)
- Streamlit page that shows the laptops as cards in a 4-column grid, each with a **View** button that opens the product page

## Files

| File | Description |
|------|-------------|
| `techno.py` | Scrapes the laptop list page and saves the data into `LaptopData.db`. |
| `app_laptop.py` | Streamlit page that reads `LaptopData.db` and shows the laptops. |

## Requirements

- Python 3
- The packages in `requirements.txt`: `requests`, `beautifulsoup4`, `pandas` and `streamlit`

## Installation

```bash
pip install -r requirements.txt
```

## Usage

The database file is not included, so run the scraper first to create it:

```bash
python techno.py
```

Then start the web page:

```bash
streamlit run app_laptop.py
```

Open the address shown in the terminal (usually `http://localhost:8501`).

## Database

`LaptopData.db`, table `laptop_techno`:

| Column | Type |
|--------|------|
| `id` | INTEGER, primary key, auto-increment |
| `description` | TEXT |
| `price` | REAL (saved as the text shown on the site, in Toman) |
| `image_url` | TEXT |
| `link` | TEXT |

## Notes

- The scraper depends on the current design (CSS classes) of the Technolife website. If the site changes, the selectors in `techno.py` must be updated.
- Every run of `techno.py` adds the products again. Delete `LaptopData.db` first if you want a clean database.
- Start the Streamlit page from the project folder, because it opens the database by its file name.

## Disclaimer

This project is for learning purposes only. Scraping a website may be restricted by its terms of service, and the product data and images belong to their owners. Use the script responsibly and do not send too many requests.
