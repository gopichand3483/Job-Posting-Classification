# **Job Listing Categorization Based on Required Skills (Hierarchical Clustering)**

This project automates the process of collecting and categorizing job listings from [karkidi.com](https://www.karkidi.com) using Hierarchical (Agglomerative) Clustering based on required skills. It clusters similar job posts by analyzing their skill requirements and stores the model for reuse in future classification or personalized job alerts.

---

## **Key Features**

* Automatically scrapes job data (title, company, location, experience, summary, and skills) from karkidi.com.
* Cleans and tokenizes the extracted skills data.
* Applies TF-IDF vectorization to the processed skills text.
* Groups jobs using Hierarchical (Agglomerative) Clustering based on skill similarities.
* Saves the trained clustering model, vectorizer, and resulting clusters for future access.
* (Optional) Supports user-specific job notifications based on skill matches.
* (Optional) Can be scheduled for daily automated scraping and clustering.

---

## **Setup Instructions**

### **Requirements**

* Python 3.7 or higher
* Required Python packages:

  * `requests`
  * `beautifulsoup4`
  * `pandas`
  * `scikit-learn`
  * `joblib`
  * `streamlit` (optional, for the UI)

Install dependencies with:

```bash
pip install -r requirements.txt
```

---

## **Usage**

### **To Run the Scraper and Perform Clustering:**

Run the following command:

```bash
python daily_scrape_and_cluster.py
```

This script will:

* Scrape job listings (default: first 2 pages; adjustable).
* Preprocess the "skills" text.
* Vectorize and cluster job posts using hierarchical clustering.
* Save:

  * The trained model (`model/karkidi_model.pkl`)
  * The TF-IDF vectorizer (`model/karkidi_vectorizer.pkl`)
  * The clustered job data (`clustered_jobs.csv`)

---

## **Streamlit App Deployment (Optional)**

The Streamlit app (`app.py`) provides a user interface to:

* Browse jobs grouped by clusters
* Filter jobs by selected clusters
* (Optionally) Enable user notifications for matching skills

To run the app locally:

```bash
streamlit run app.py
```

---

## **Automation (Optional)**

To automate daily scraping and clustering:

* Use **cron jobs** (Linux/macOS) or **Task Scheduler** (Windows) to run `daily_scrape_and_cluster.py`.
* Alternatively, set up a **GitHub Actions** workflow to execute the script and push updated data.

Once the script runs, the Streamlit app will reflect the updated clusters automatically.

---

## **Project Directory Structure**

```
your-repo/
├── daily_scrape_and_cluster.py   # Core script for scraping and clustering
├── app.py                        # Streamlit web app
├── clustered_jobs.csv            # CSV with latest clustered job data
├── model/
│   ├── karkidi_model.pkl         # Saved clustering model
│   └── karkidi_vectorizer.pkl    # TF-IDF vectorizer
├── requirements.txt              # List of dependencies
└── README.md                     # Project documentation
```

---
