**Carbon Footprint Optimization using ML**

Team:

Frank Vocatura

# Business Opportunity/Problem

**Problem:** Carbon Emissions have been a focal point for enterprises to combat climate pollution. Regulations have been getting stricter and us as consumers wish for sustainability. By having a platform to monitor, visualize and create strategies for emissions reduction.

**Opportunity:** Use AI to create a platform to monitor emissions, simulate strategies and automate reporting. Gain knowledge of using open-source technologies to create this platform (satellite imagery, IoT sensors etc.) Of course, gain extensive knowledge with training LLMs AIs.

# Users

In a perfect world my platform would be used by supply chain management and suppliers (and more). Supply chain management roles would be to optimize logistics and strategies, balancing cost and efficiency. The platform proposed would help companies manage carbon emissions, cost and risk. Using this platform will utilize RL to simulate managing suppliers to find a good balance between cost and emissions. For example, a workflow could look something like using the platform to analyze suppliers, run a simulation using RL to reroute shipments to avoid an extremely high emission scenarios, then moving to that new supplier.

Suppliers’ role is to provide said materials to larger enterprises and compete with others on emissions and cost (mainly cost). With the growing pressure on sustainability, some suppliers may focus more on emissions. With the platform suppliers could use tools like an emission calculator to assess these factors. Utilizing RL to recommend improvements on transporting as well.

Also, the platform could just be used by a basic user as a tool to visualize emissions/carbon footprints of companies.

# High-Level Users

1. Track Real-Time emissions
    1. Track emissions using satellite imagery
    2. Companies can track routes and analyze for cost/emissions trade off
    3. Manage real-time data and archive routes to analyze performance.
2. Supply Chain Analysis
    1. Analyze suppliers’ routes and emissions
    2. Find the best route to strike a healthy balance between cost, time and emissions.
    3. Manage real-time data and archive routes to analyze performance.
3. Simulations
    1. Run “What-ifs” using RL
    2. Archive routes to analyze performance and identify poorly optimized routes.
    3. Feed the AI more data to enhance the RL outpus.
4. Compliance Reporting(optional)
5. Integration
    1. APIs to be used openly among other platforms

# Tech Stack/Approach

Core AI Components (High-Level)

1. **Satellite Imagery**:
    1. **Tech:** Vision Transformers which is fine tuned on methane data (Sentinel-5P).
    2. **Output:** Real-time detection of emissions and emission hotspots.
2. **NLP for Human Interaction:**
    1. **Tech:** Mistal (Possible) which is fine tuned to extract specific sustainability clauses.
    2. **Output:** Supplier risk/strategies
3. **Optimization:**
    1. **Tech:** Baseline3 for RL. Balancing cost, emissions and risk
    2. **Output:** Recommendations based on parameters.

**Tech Stack (High-Level):**

1. **Frontend:**
    1. **Dashboard + Visuals:** Streamlit (Python), Ploty
    2. **Maps:** Leaflet, GeoPandas(Python)
    3. **Design:** Tailwind/MaterialUI
2. **Backend:**
    1. **API:** FastAPI, Redis
    2. **DB:** PostgreSQL + PostGIS (Geo queries). TimescaleDB
    3. **Auth(?): JWT**
    4. **Workflow:** Apache
3. **ML:**
    1. **Sat. Imagery:** Google Earth Engine, Hugging Face transformers, OpenCV
    2. **NLP:** Mistral7b (Fine Tuning), Spacy (Entity recognition)
    3. **RL:** Baseline3
    4. **Data Process:** Pandas/NumPy
    5. **MLOps:** MLFlow
4. **Cloud:**
    1. **Provider:** AWS, Google Cloud
    2. **Docker**
    3. **CI/CD:** GitHub/Lab
    4. **Monitor:** Jenkins(?), Prometheus
5. **Miscellaneous/Open Source**
    1. **TBD**
6. **Languages:**
    1. Python. SQL, JS, Bash

# High-Level DB Architecture

Potential Data types:  
Geospatial: Sat. Imagery, cords

Text: Contracts, Reports

Time: Metrics, Sensor Data.