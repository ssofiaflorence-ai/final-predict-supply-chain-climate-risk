
# Predicting Climate-Induced Supply Chain Delays: Proactive Risk Mitigation in Transit Logistics

An end-to-end Machine Learning and Geospatial Analytics framework designed to forecast climate-induced transit bottlenecks, optimize Estimated Delivery Dates (EDDs), and enable proactive rerouting before operational disruptions occur.

---

## 📌 Project Overview

Severe weather events and extreme climate shifts create unpredictable bottlenecks across global trade corridors. Traditional logistics frameworks rely on reactive damage control after a delay occurs. 

This project shifts logistics management from reactive to **proactive risk mitigation**. By fusing historical shipment records with real-time NOAA/OpenWeather data and infrastructure telemetry, the model forecasts delay probabilities and time-to-disruption along active transit routes, empowering logistics managers to dynamically reroute high-value inventory.

---

## 🏗️ Data Architecture & Sources

The project integrates three primary data streams:

* **Historical Shipping & Transit Logs**: Origin-destination pairs, carrier tracking, historical delivery timelines, and high-value cargo designations.
* **NOAA & OpenWeather API Data**: Real-time and forecasted meteorological telemetry, including precipitation levels, wind speeds, extreme temperature variations, and storm tracks.
* **Geospatial & Infrastructure Records**: Route waypoints, port throughput capacities, highway choke points, and regional infrastructure risk indicators.

---

## ⚙️ Methodology & Machine Learning Architecture

1. **Geospatial Mapping & Feature Engineering**:
   * Spatial matching of active shipment routes with dynamic weather grids using spatial join algorithms.
   * Extraction of regional weather severity indices, environmental vulnerability metrics, and bottleneck risk indicators.

2. **Predictive Modeling**:
   * **Supervised Learning**: Ensembled tree-based classifiers (**Random Forest**, **XGBoost**) to predict dynamic delay probabilities and classify transit disruption severity.
   * **Survival Analysis**: Time-to-event modeling (e.g., Cox Proportional Hazards) to estimate expected duration of weather-induced hold-ups along specific transit legs.

3. **Risk Mitigation Pipeline**:
   * Machine learning-driven risk scoring to trigger dynamic rerouting recommendations for shipments exceeding risk thresholds.

---

## 📂 Repository Structure
├── data/
│   ├── raw/                  # Raw shipping logs & infrastructure data
│   ├── processed/            # Weather-merged feature matrices
│   └── spatial/              # Route shapefiles & weather grids
├── notebooks/
│   ├── 01_data_ingestion.ipynb
│   ├── 02_geospatial_feature_engineering.ipynb
│   ├── 03_model_training_classification.ipynb
│   └── 04_survival_analysis_eval.ipynb
├── src/
│   ├── data_pipeline.py      # NOAA/OpenWeather ingestion & spatial matching
│   ├── features.py           # Feature extraction & data normalization
│   └── models.py             # Model definitions (XGBoost, Random Forest, CoxPH)
├── config/
│   └── config.yaml           # API keys, pathing, and model hyperparameters
├── README.md
└── requirements.txt


---

## 🔧 Prerequisites & Installation

Ensure you have Python 3.9+ installed along with the required spatial and machine learning libraries:

```bash
# Clone the repository
git clone [https://github.com/your-username/climate-supply-chain-delays.git](https://github.com/your-username/climate-supply-chain-delays.git)
cd climate-supply-chain-delays

# Install dependencies
pip install -r requirements.txt
Core Libraries Used:
Data Processing & ML: pandas, numpy, scikit-learn, xgboost

Geospatial Processing: geopandas, shapely, folium

Survival Analysis: lifelines

Weather Ingestion: requests (OpenWeather API integration)

🚀 How to Run
Configuration: Add your OpenWeather API credentials and update directory paths in config/config.yaml.

Data Pipeline & Spatial Merging:

Bash
python src/data_pipeline.py
Model Training & Evaluation: Run the modeling notebooks in notebooks/ or execute the training script:

Bash
python src/models.py
🛣️ Roadmap & Future Enhancements
[ ] API Integration: Connect directly to real-time carrier GPS feeds for continuous risk re-scoring.

[ ] Dynamic Route Optimization: Integrate graph algorithms (e.g., A* or Dijkstra's algorithm modified with weather risk weights) to automate proactive rerouting.

[ ] IoT Sensor Fusion: Incorporate real-time cargo environmental metrics (container temperature, humidity) for sensitive goods.
