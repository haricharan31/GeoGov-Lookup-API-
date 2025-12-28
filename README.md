# 🗽 GeoGov Lookup API – Find U.S. Representatives via ZIP Code

**GeoGov Lookup API** is a prototype service that provides details about political representatives for a specified **U.S. ZIP code**.  
It combines database modeling, web scraping, **Flask-based API development**, and simple **LLM-aided data extraction**.

---

## ✨ Key Highlights

- **Well-defined Database Model** covering:
  - Geographic Info (ZIP, City, State, District)
  - Politicians (Name, Designation, Party, Government Branch)
  - Relationship Mapping between regions & officials
- **Simple REST API endpoint**
  - Input: ZIP Code (ex: `zip=11354`)
  - Output: Representative info in JSON format
- **Automated Data Collection**
  - Scraping via `BeautifulSoup`
  - Processing using **Google Gemini API**
- **Proof-of-Concept**
  - Includes working examples for limited ZIP codes

---

## 🧱 Project Layout

```
├── app.py                 # Flask API for representative lookups
├── scraper_gemini.py      # Web scraper + LLM parsing + DB update
├── setup_database.py      # Creates SQLite DB and inserts base records
├── geogov_lookup.db       # Generated SQLite database
├── requirements.txt       # Required Python packages
└── README.md              # This project guide
```

---

## 🛠️ Getting Started

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/<your-username>/geogov-lookup-api.git
cd geogov-lookup-api
```

### 2️⃣ Optional: Create a Virtual Environment
```bash
python -m venv venv
source venv/bin/activate  # macOS/Linux
venv\Scripts\activate     # Windows
```

### 3️⃣ Install Dependencies
```bash
pip install -r requirements.txt
```

### 4️⃣ Configure API Key
Add a `.env` file:
```env
GOOGLE_API_KEY=your_google_gemini_api_key_here
```

### 5️⃣ Initialize the SQLite Database
```bash
python setup_database.py
```

### 6️⃣ Scrape Test Data (Optional)
```bash
python scraper_gemini.py
```

### 7️⃣ Run the Server
```bash
python app.py
```
Access API at: `http://127.0.0.1:5000`

---

## 🔍 API Reference

**GET Endpoint**
```
/representatives?zip=<ZIP_CODE>
```

### Sample Call
```
GET http://127.0.0.1:5000/representatives?zip=11354
```

### Possible JSON Output
```json
{
  "zip": "11354",
  "representatives": [
    { "name": "Grace Meng", "title": "U.S. House Rep, NY-6" },
    { "name": "Chuck Schumer", "title": "U.S. Senator, NY" },
    { "name": "Kathy Hochul", "title": "Governor, New York" }
  ]
}
```

---

## 🧩 Database Overview

Tables included:

| Table Name | Purpose |
|-----------|---------|
| **geography** | ZIP, city, state, district info |
| **representatives** | Stores politician details |
| **rep_geography_map** | Relationship mapping table |

---

## 🧰 Technologies Used

- **Python** (Flask, Requests, BeautifulSoup)
- **SQLite** as embedded database
- **Google Gemini** for intelligent text extraction

---

## 👤 Maintainer

**Your Name**  
GitHub: [@haricharan31](https://github.com/haricharan31)
