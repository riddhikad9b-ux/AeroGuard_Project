# 🛡️ Aéro Guard

**Aéro Guard** is an intelligent environmental exposure tracking and route-planning application designed for daily commuters. It calculates real-time personal exposure scores based on particulate matter ($\text{PM}_{2.5}$), temperature, and transit mode (such as two-wheelers or cars) to help users make healthier commute choices.

---

## 🚀 Key Features

* **Real-Time Environmental Tracking:** Integrates with the OpenWeather API to pull live air pollution ($\text{PM}_{2.5}$, $\text{PM}_{10}$) and weather metrics.
* **Commute Exposure Scoring Engine:** Computes a custom 0–100 risk index weighted by transit mode (e.g., higher direct exposure on two-wheelers vs. cars).
* **Interactive Route Mapping:** Visualizes commutes (e.g., Porur to Guindy, Chennai) using interactive Folium maps with environmental overlays.
* **Historical Logging & Analytics:** Automatically logs session data into structured CSVs and generates weekly exposure trend charts.
* **Personalized Safety Recommendations:** Dynamically suggests protective measures (such as masks, sunscreens, or timing adjustments).
* **FastAPI Backend Wrapper:** Built-in REST API endpoints ready to connect with mobile frontends (React Native / Flutter).

---

## 🛠️ Tech Stack

* **Backend & Logic:** Python, Pandas, NumPy, Requests
* **Geospatial & Mapping:** Folium, Geopandas, Shapely
* **API Framework:** FastAPI, Uvicorn
* **APIs:** OpenWeather Air Pollution & Geocoding APIs

---

## 📂 Project Structure

```text
AeroGuard_Project/
│
├── data/
│   └── commute_history.csv       # Logged commute sessions and historical metrics
├── models/                       # Scoring and recommendation logic modules
├── exports/                      # Generated visual reports and trend charts
└── app.py                        # FastAPI server backend
