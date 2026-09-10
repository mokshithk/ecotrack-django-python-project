# EcoTrack — Corporate Carbon Footprint Intelligence Platform 🌿⚡

**EcoTrack** is an enterprise-grade, full-stack carbon auditing and sustainability management application built with **Python** and **Django**. Designed to transform raw operational data into actionable environmental intelligence, EcoTrack allows organizations to aggregate multi-department resource consumption, calculate carbon footprints using standardized Greenhouse Gas (GHG) Protocol factors, track carbon budget goals, and generate AI-driven strategic reporting.

---

## 🌟 Key Features & Capabilities

* **Role-Based Access Control (RBAC):**
  * **Org Admin:** Oversees organization-wide analytics, establishes corporate sustainability targets, reviews departmental league tables, and accesses automated AI reports.
  * **Department Managers:** Log localized operational resource data (electricity, petrol, diesel, logistics) and monitor branch-level efficiency targets.

* **Interactive Data Visualizations (Chart.js):**
  * **6-Month Emissions Trajectory:** Dynamic HTML5 canvas line graph displaying monthly emission trends.
  * **Department League Tables:** Comparative ranking of top-emitting divisions to pinpoint reduction opportunities.
  * **Resource Breakdowns:** Categorical contribution charts showing emission sources.

* **Automated AI Intelligence Layer:**
  * Integrates the **Google Gemini API** to analyze system telemetry and output a structured 3-part **Strategic Performance Report** (Executive Summary, Key Drivers, and 30-Day Action Plan).
  * **Performance Optimization:** Built-in **6-Hour Time-To-Live (TTL) Caching Layer** with manual force-refresh (`?refresh=1`) to eliminate latency and preserve API quotas.

* **Dynamic Carbon Budgeting:**
  * Live carbon target progress bar calculating real-time usage against active organizational goals.

---

## 📐 Carbon Calculation Methodology

EcoTrack computes carbon equivalent emissions ($\text{CO}_2\text{e}$) using the universal carbon accounting formula:

$$\text{Carbon Emissions (kg CO}_2\text{e)} = \text{Activity Data} \times \text{Emission Factor}$$

### Baseline Emission Coefficients
* **Electricity:** $0.4\text{ kg CO}_2\text{e per kWh}$
* **Petrol:** $2.3\text{ kg CO}_2\text{e per Liter}$
* **Diesel:** $2.7\text{ kg CO}_2\text{e per Liter}$

---

## 🛠️ Technology Stack

| Layer | Technology |
| :--- | :--- |
| **Backend Framework** | Python 3.13, Django Web Framework (MVT Architecture) |
| **Database** | SQLite (Development) / PostgreSQL-ready (`dj-database-url`) |
| **Frontend UI** | HTML5, Custom CSS3 (Obsidian & Emerald Matrix Theme), Bootstrap 5 |
| **Data Visualizations** | Chart.js (via CDN) |
| **AI Integration** | Google Gemini API (`google-genai` SDK) |
| **Server Middleware** | Gunicorn, WhiteNoise (Static Assets) |

---

## 📂 System Architecture

```text
EcoTrack/
│
├── core/                   # Main Application Package
│   ├── models.py           # Database Schemas (Organization, Department, ActivityLog, Goal)
│   ├── views.py            # Business Logic, Analytics, AI Caching, & Auth
│   ├── urls.py             # Route URL patterns
│   └── templates/          # Responsive HTML Dashboards (Admin & Manager)
│
├── static/                 # Stylesheets, Custom JS Scripts, & UI Assets
├── manage.py               # Django CLI Script
├── requirements.txt        # Project Dependencies
└── README.md               # Repository Documentation

```
🚀 Local Installation & Setup
Prerequisites
Python 3.10+ installed

Git installed

Step-by-Step Setup
Clone the Repository:

Bash
git clone [https://github.com/mokshithk/EcoTrack.git](https://github.com/mokshithk/ecotrack-django-python-project)
cd EcoTrack
Create & Activate a Virtual Environment:

Bash
python -m venv env

# On Windows:
env\Scripts\activate

# On macOS/Linux:
source env/bin/activate
Install Dependencies:

Bash
pip install -r requirements.txt
Configure Environment Variables:
Create a .env file in the root directory:

Code snippet
SECRET_KEY=your_django_secret_key
DEBUG=True
GEMINI_API_KEY=your_google_gemini_api_key
Run Database Migrations:

Bash
python manage.py migrate
Create an Admin Superuser:

Bash
python manage.py createsuperuser
Launch Development Server:

Bash
python manage.py runserver
Navigate to http://127.0.0.1:8000/ in your browser.
