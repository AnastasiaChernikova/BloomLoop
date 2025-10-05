# 🌍 **BloomLoop 2025 NASA Space Apps Challenge**

> **Challenge:** [BloomWatch: An Earth Observation Application for Global Flowering Phenology](https://www.spaceappschallenge.org/2025/challenges/bloomwatch-an-earth-observation-application-for-global-flowering-phenology/)  
> **Team:** Anastasia&Cat 

---

### 🌸 Overview

**BloomLoop** is a data-driven notebook that connects **satellite Earth Observation (Sentinel-2)** with **citizen-science observations** (Pl@ntNet via GBIF and iNaturalist) to analyze and predict **global flowering dynamics**.  

The model extracts NDVI/NDYI vegetation indices, detects seasonal breaks (phenological changes), and applies a **Random Forest classifier** to estimate bloom events.  

**Outputs include:**
- Interactive **map of bloom sites** (`map_final.html`)
- **NDVI/NDYI time-series visualization**
- **Bloom prediction report**

---

### ⚙️ Requirements

- Python **3.10+**
- [Anaconda](https://www.anaconda.com/download) or [Miniconda](https://docs.conda.io/en/latest/miniconda.html)
- [Google Earth Engine access](https://developers.google.com/earth-engine/cloud/registration)
- Internet connection (for API calls to GBIF, iNaturalist, Sentinel-2)

---

### 🚀 Installation & Setup

#### 1️⃣ Clone this repository
```bash
git clone https://github.com/AnastasiaChernikova/BloomLoop.git
cd BloomLoop
```

#### 2️⃣ Create and activate a conda environment
```bash
conda create -n bloomloop python=3.10 -y
conda activate bloomloop
```

#### 3️⃣ Install dependencies
```bash
conda install -c conda-forge geopandas pandas numpy matplotlib folium requests ruptures scikit-learn seaborn jupyterlab earthengine-api -y
```

#### 4️⃣ Launch Jupyter Notebook
```bash
jupyter lab
# or
jupyter notebook
```
Then open **`BloomLoop.ipynb`**

---

### 🌐 Google Earth Engine Setup

BloomLoop uses the **Earth Engine Python API** to retrieve Sentinel-2 NDVI/NDYI data.

1. **Authenticate your account**
   ```python
   import ee
   ee.Authenticate()
   ```
   A browser window will open — log in with your Google account that has Earth Engine access.

2. **Initialize with your project ID**
   Replace this line in the notebook:
   ```python
   ee.Initialize(project='ee-requestanastasiachernikova')
   ```
   with **your own Earth Engine project ID**, for example:
   ```python
   ee.Initialize(project='ee-yourprojectid')
   ```
   > ⚠️ This step is required — otherwise Earth Engine requests will fail.

---

### 🧠 Run the Analysis

1. Run **each cell sequentially** in `BloomLoop.ipynb`:
   - Step 1: Connect to Earth Engine  
   - Step 2: Load GeoJSON (`WildflowerBlooms_AreaOfInterest.geojson`)  
   - Step 3–4: Fetch Pl@ntNet + iNaturalist bloom observations  
   - Step 5–6: Retrieve Sentinel-2 NDVI/NDYI indices  
   - Step 7: Detect phenological breaks (BFAST)  
   - Step 8: Visualize data and save `map_final.html`  
   - Step 9: Train and evaluate Random Forest classifier  

2. Wait for outputs to appear:
   - 📊 NDVI/NDYI charts  
   - 🗺️ `map_final.html` (interactive map)  
   - 🧩 Classification report and confusion matrix  

---

### 📂 Repository Contents

| File | Description |
|------|--------------|
| `BloomLoop.ipynb` | Main notebook with full workflow |
| `WildflowerBlooms_AreaOfInterest.geojson` | Sample input polygons for bloom regions |
| `map_final.html` | Generated interactive bloom map (output) |
| `README.md` | Documentation and setup instructions |

---

### 🧭 Outputs

- **NDVI/NDYI time-series plot** – compares vegetation indices over time  
- **Break detection visualization** – identifies likely bloom periods  
- **Interactive map (`map_final.html`)** – displays observation sites  
- **Random Forest classification report** – accuracy and bloom detection metrics

---

### 🛠️ Troubleshooting

| Issue | Fix |
|-------|-----|
| `ee.Authenticate()` fails | Re-run cell, ensure browser opens and correct Google account used |
| `EEException: Project not found` | Replace project ID with your own in `ee.Initialize(...)` |
| `ModuleNotFoundError` | Reinstall missing package via `conda install -c conda-forge <package>` |
| `GDAL / GeoPandas errors` | Use conda-forge channel only for geospatial packages |
| Notebook stuck on API request | Re-run cell or reduce years/radius parameters |

---

### 🛰️ Data Sources

- 🌿 **Pl@ntNet via GBIF API** — plant occurrence records  
- 🌸 **iNaturalist API** — flowering observations  
- 🛰️ **Copernicus Sentinel-2 SR** — NDVI/NDYI vegetation indices  

---

### 💡 Why It Matters

Understanding **flowering phenology** is essential for tracking:
- Climate change impacts  
- Pollinator interactions  
- Agricultural cycles  
- Biodiversity patterns  

By merging ground observations with satellite time series, **BloomLoop** creates a scalable framework for **global bloom monitoring**.

---

### 🧾 Citation

If you reuse this notebook or its workflow, please cite:
```
Chernikova, A. (2025). BloomLoop: An Earth Observation Application
```
