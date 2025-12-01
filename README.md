# Resume Information Extractor

## Project Overview

The **Resume Information Extractor** is a web-based application designed to process resumes (unstructured text) and automatically extract key information such as:

* `resume_id`
* `Category`
* `email`
* `phone`
* `skills`
* `experience_years`
* `education`

The extracted data is stored in a **SQLite database** and can also be exported to a **CSV file**. Additionally, the project provides **visualizations** to give insights on the processed resumes, such as experience distribution, skill frequencies, and contact availability.

This project demonstrates practical automation for **HR/ATS pipelines** and serves as a strong placement-ready project.

---

## Features

1. **Resume Preprocessing**

   * Cleans raw text to remove unwanted characters, emojis, HTML tags, and formatting issues.
   * Normalizes bullets, dashes, and spacing.

2. **Information Extraction**

   * **resume_id** - Unique identifier assigned to each uploaded resume.
   * **Category** - The category or type of resume (if applicable).
   * **email** - Extracts valid email addresses from the resume text.
   * **phone** - Extracts valid international phone numbers, ignoring dates and years.
   * **skills** - Extracts technical and professional skills, including lists and separated phrases.
   * **experience_years** - Extracts total years of experience mentioned in the resume.
   * **education** - Extracts degrees, universities, and years of graduation.

3. **Data Storage**

   * Saves processed resumes in **SQLite database** (`resume_database.db`).
   * Can export to **CSV** (`resume_final_output.csv` or `resume_final_parallel.csv`).

4. **Visualizations**

   * **Bar charts** for top skills.
   * **Pie charts** for email and phone availability.
   * **Experience distribution** charts.
   * **Word cloud** for skills visualization.

5. **Parallel Processing**

   * Handles multiple resumes in parallel to speed up extraction for large datasets.

---

## Project Structure

```bash
resume_extractor_web/
│
├── app.py # Flask backend
├── requirements.txt # Python dependencies
├── config.py # Config variables
├── utils.py # Extraction functions
├── resume_database.db # SQLite database
├── static/ # CSS, JS, images
│ ├── css/
│ │ └── style.css
│ ├── js/
│ │ └── scripts.js
│ └── images/
├── templates/ # HTML templates
│ ├── layout.html
│ ├── index.html
│ └── visualize.html
├── uploads/ # Uploaded resumes
└── README.md
```

---

## Installation

1. Clone the repository

```bash
git clone <your-repo-url>
cd resume_extractor_web

```
2. Create a virtual environment

```bash
python -m venv venv
source venv/bin/activate        # Linux/Mac
venv\Scripts\activate           # Windows
```
3. Install dependencies

```bash
pip install -r requirements.txt
```

Usage

**1. Run the Flask app**

```bash
python app.py
```
**2. Open your browser and go to**

```bash
[python app.py](http://127.0.0.1:5000/)
```
**3. Upload Resumes**

* Upload one or multiple `.txt` files containing resumes.
* The system will preprocess, extract, and save the data.

**4. View Visualizations**

Navigate to the **Visualize** page to see metrics and charts:

* Total resumes processed
* % of resumes with email and phone
* Average skills per resume
* Unique skills count
* Experience distribution
* Top skills bar chart
* Skills word cloud

**5. CSV/Database**

* All extracted data is saved to `resume_database.db` (SQLite).
* You can export the same data to CSV using the provided export functionality.

## Example CSV Output

| resume_id | Category   | email                | phone       | skills                          | experience_years | education                      |
| ---------- | ---------- | ------------------  | ----------- | ------------------------------- | ---------------- | ------------------------------ |
| 1          | IT        | john@example.com    | +1234567890 | ["Python", "SQL", "Django"]     | 5                | ["B.Sc Computer Science 2019"] |
| 2          | Development | jane@example.com    | +1987654321 | ["JavaScript", "React", "Node"] | 3                | ["B.Tech IT 2020"]             |

## Metrics & Insights

* **Resumes processed:** Total number of resumes uploaded.
* **% with Email / Phone:** Percentage of resumes containing valid email or phone.
* **Average Skills per Resume:** Number of skills per resume.
* **Distribution of Experience Years:** Bar chart showing how many candidates have 0–10+ years of experience.
* **Unique Skills:** Count of unique skills across all resumes.
* **Top Skills & Word Cloud:** Most common skills visualized using bar charts and word clouds.

## Notes

* Works primarily with **plain text resumes**. PDF parsing can be added in future versions.
* Parallel processing is used for faster extraction on large datasets.
* Skills are normalized and cleaned to remove special characters, bullets, and emojis.

## Future Improvements

* Add **PDF/Word resume support**.
* Integrate **full-stack UI** with search/filter functionality.
* Enable **real-time dashboard updates**.
* Add **export to Excel** with formatted sheets.
