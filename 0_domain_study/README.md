# Domain Study – Satellite Tracking & Observation Ecosystem

## 📚 Overview  
This README provides a structured summary of the **domain study** behind satellite observation analysis, with a focus on the **SatNOGS open-source global ground station network**. It consolidates background research, technical concepts, industry context, and key findings that support further analysis and machine learning modeling.

---

## 📁 Contents  
This domain study covers the following materials:

- **satellite_communications_basics** – Fundamentals of satellite communication  
- **satnogs_architecture** – SatNOGS network structure and components  
- **observation_challenges** – Common issues in satellite tracking  
- **signal_quality_factors** – Parameters affecting observation success  
- **literature_review** – Academic and technical references

---

## 🎯 Research Questions
1. What factors most significantly affect satellite observation success?  
2. How does ground station configuration impact signal quality?  
3. What temporal and geometric patterns exist in successful observations?  
4. How can machine learning optimize ground station scheduling and operations?

---

## 📡 SatNOGS Ecosystem

The **SatNOGS (Satellite Networked Open Ground Station)** project is an open-source, community-driven global network of satellite ground stations. It was developed by the **Libre Space Foundation (LSF)** to democratize space communications and enable affordable access to satellite data.

SatNOGS provides fully open-source tools for **tracking, receiving, processing, storing, and sharing satellite downlink data**.

---

# 🛰️ 1. SatNOGS Architecture Overview

SatNOGS is composed of **four major layers**:

## **1.1. Ground Station Hardware Layer**
Community-operated ground stations typically include:
- **Antenna systems**: Yagi, helical, dipole, QFH, turnstile  
- **Rotators**: For elevation–azimuth tracking (optional; many stations use fixed antennas)  
- **RF Front-End**  
  - LNAs (Low Noise Amplifiers)  
  - SAW/LC filters  
  - Bias-T modules  
- **SDR Receivers**: RTL-SDR, LimeSDR, PlutoSDR, HackRF  
- **Raspberry Pi / Linux Host** running `satnogs-client`

Many stations are low-cost (<200 EUR), making the network extremely accessible.

---

# 🌐 2. Network Architecture

## **2.1. SatNOGS Network**
The distributed ground stations communicate with a **centralized scheduling platform**:

**Components**
1. **SatNOGS Network Frontend**  
   - Web interface for scheduling, reviewing observations, and browsing satellites.
2. **Scheduler & Task Generator**  
   - Automatically assigns observations to available stations.
3. **Station Dashboard**  
   - Shows status, health, uptime, waterfall previews.
4. **API**  
   - REST endpoints for observation data, telemetry, satellites, transmitters, etc.

## **2.2. SatNOGS Client**
On each ground station, the SatNOGS client handles:
- Receiving scheduled passes
- Driving rotators
- Configuring SDR frequency & bandwidth
- Capturing RF data
- Generating waterfall and audio
- Uploading results to the network

The client is built on:
- **GNU Radio**
- **Python**
- **Docker / Ansible deployment support**

---

# 📥 3. Data Pipeline & Processing

## **3.1. Observation Lifecycle**
1. **Scheduler selects a satellite pass**  
2. **Client prepares station hardware** (tracking, tuning, demod settings, RX gain)  
3. **RF Capture:** I/Q → audio → waterfall  
4. **Local processing:** demodulation, signal detection  
5. **Upload to Network server**  
   - *Waterfall images*  
   - *Audio recordings*  
   - *RF metadata*  
6. **Optional Telemetry Decoding** via  
   - SatNOGS Decoders  
   - gr-satellites  
   - Community pipelines (AMSAT, university cubesats)

## **3.2. Waterfall Processing**
SatNOGS stores waterfall spectrograms as compressed images. These are used for:
- Visual quality assessment ("Waterfall Status")
- Machine learning signal classification
- Detecting Doppler shift curves
- Identifying carrier presence or interference

## **3.3. Telemetry Decoding Ecosystem**
Decoding happens via:
- **SatNOGS DB Autodecoders**
- **Community decoders**
- **External tooling**: GNURadio, STRF, DSP chains  

Decoded telemetry is forwarded to:
- Mission teams
- Community dashboards
- SatNOGS DB satellite pages

---

# 📊 4. Data Infrastructure

## **4.1. SatNOGS Database (DB)**  
Stores:
- Observation metadata  
- Waterfall images  
- Telemetry packets  
- Satellite transmitter metadata  

API endpoints include:
- **/observations/**
- **/satellites/**
- **/transmitters/**
- **/ground_stations/**

The database currently contains:
- **12.5+ million observations**
- Thousands of satellites and transmitters
- Over 600 active ground stations worldwide

---

# 🌍 5. Community Network

The SatNOGS community is one of the largest open RF communities globally.

## **Worldwide Stations**
- >600 active  
- >2,500 registered  
- Countries represented: **100+**  
- Daily observations: **20,000–40,000**

## **Community Governance**
Managed by the **Libre Space Foundation**, with:
- Open-source development
- Volunteer maintainers
- University and research partnerships

## **Typical Contributors**
- Amateur radio operators  
- Space engineering students  
- CubeSat developers  
- Research institutions  
- RF hobbyists  

---

# 🛰️ 6. Supported Satellite Types

SatNOGS supports tracking and decoding for:
- **CubeSats (1U–12U)**  
- **LEO missions**  
- **NOAA / METEOR weather satellites**  
- **AIS (ship tracking)**  
- **ADS-B (aircraft)** via extensions  
- **Amateur radio satellites**  
- **University missions**  
- **STEM educational satellites**

Bands frequently used:
- **VHF** (137–150 MHz)  
- **UHF** (400–450 MHz)  
- **S-band** (2200–2300 MHz)  
- Experimental bands (as approved by local regulations)

---

# 🧩 7. Scheduling Logic & Constraints

The scheduler considers:
- Pass geometry (max elevation, duration, timing)
- Station availability & location
- Satellite transmitter activation windows
- Conflict resolution across nearby stations
- Priorities (important missions, decoding campaigns)

Machine learning–driven scheduling is an emerging research area.

---

# 🛠️ 8. SatNOGS Tooling Ecosystem

### **SatNOGS Client**  
Ground station controller software.

### **SatNOGS Network**  
Scheduling engine + observation viewer.

### **SatNOGS DB**  
Metadata repository for satellites & transmitters.

### **SatNOGS Analyzer**  
Tools for:
- Waterfall analysis  
- Spectrum feature extraction  
- Autocorrelation and Doppler analysis  

### **Dockerized Ground Station Setup**
A ready-to-deploy containerized environment.

---

# 🔍 9. Why SatNOGS is Unique

| Feature | SatNOGS | Commercial Stations (AWS / KSAT) |
|--------|---------|----------------------------------|
| Open-source | ✔ | ✖ |
| Crowd-operated | ✔ | ✖ |
| Free access | ✔ | ✖ |
| Global dense coverage | ✔ | Limited |
| Educational mission | ✔ | ✖ |
| Support for hobby/amateur missions | ✔ | ✖ |

SatNOGS is **the only fully open, global RF sensing network**.

---

# ⚡ 10. Relevance to Machine Learning

SatNOGS data is ideal for ML applications:
- Predicting observation success  
- RF signal classification  
- Waterfall image classification  
- Pass quality prediction  
- Scheduling optimization  
- Detecting interference patterns  
- Anomaly detection in satellite behavior  

This project fits naturally into emerging research around:
- **automated signal identification**
- **predictive scheduling**
- **network resource optimization**

---

## 🔬 Key Technical Concepts

### Satellite Pass Parameters  
- **Elevation / Azimuth** – Satellite position relative to station  
- **Pass Duration** – Visibility window length  
- **Max Altitude** – Highest elevation; strongly correlated with signal quality  
- **Rise/Set Azimuth** – Horizon crossing points  

### Signal Quality Factors
1. **Geometric** – Elevation angle, distance, atmospheric path length  
2. **Environmental** – Weather, interference, absorption  
3. **Equipment** – Antenna gain, receiver sensitivity, calibration  
4. **Orbital** – Satellite power, orientation, frequency band  

---

## 📊 Data Sources

### Primary SatNOGS Data
- **12.5M+ observations** from global ground stations  
- **TLE orbital data** (Space-Track)  
- **Station metadata** (equipment, geolocation, antenna types)

### Key Database Tables  
- **base_observation** – Core observation records  
- **base_station** – Ground station info  
- **base_satellite** – Satellite metadata  
- **base_transmitterentry** – Transmitter frequency and power details  

---

## 🎯 Observation Success Indicators  
- **Status Codes**: 100 = Good, -100 = Bad, 0 = Unknown  
- **Waterfall Status** – Visual quality assessment  
- **Telemetry Decoding** – Successful data extraction  
- **Signal Metrics** – SNR, signal strength, noise floor  

---

## 📈 Industry Context

### Similar Systems  
- NASA DSN – Deep-space communications  
- ESA ESTRACK – European tracking network  
- AWS Ground Station / KSAT – Commercial cloud-integrated services  

### Use Cases  
- Space Situational Awareness (SSA)  
- Earth observation  
- Amateur radio & educational missions  
- Emergency and disaster communication  

---

## 🔍 Literature Review Highlights  

### Key Papers  
1. **Machine Learning for Satellite Communication (IEEE, 2022)** – RF classification ~85% accuracy; SNR key feature  
2. **Optimizing Ground Station Networks (SpaceOps, 2021)** – Genetic algorithm scheduling → ~30% improvement  
3. **SatNOGS: An Open Ground Station Network (FOSDEM, 2020)** – Architecture overview, community growth  

### Analytical Techniques  
- Time Series Analysis, Geospatial Analysis, Signal Processing, Machine Learning

---

## 🛠️ Practical Implications  

### Ground Station Operators
- Prioritize high-success passes, optimize antennas, schedule maintenance smartly

### Network Managers
- Improve resource allocation, prevent bottlenecks, monitor performance trends

### Satellite Operators
- Maximize successful downlinks, identify optimal visibility windows, support mission planning

---

## 📚 Additional Resources

### Documentation
- [SatNOGS Wiki](https://wiki.satnogs.org/)  
- [Libre Space Documentation](https://libre.space/docs/)  
- [SatNOGS API Documentation](https://network.satnogs.org/api/)  

### Community
- [SatNOGS Forum](https://community.libre.space/c/satnogs/6)  
- [Observation Reports](https://community.libre.space/c/satellites-observations/16)  
- [GitHub Repositories](https://github.com/satnogs)  

### Learning
- [ESA Satellite Communications Basics](https://www.esa.int/Enabling_Support/Space_Engineering_Technology/ESA_Satellite_Communications_Basics)  
- [AMSAT Amateur Satellite Guide](https://www.amsat.org/wordpress/)  
- [GNU Radio](https://www.gnuradio.org/) – Signal processing

---

## 🎓 Academic Value  
- Technical Understanding of satellite communication  
- Correct interpretation of SatNOGS observations  
- Problem framing for ML tasks  
- Model design informed by domain constraints  

---

### ➡️ Next Step  
Proceed to **`1_datasets/`** for data acquisition and preparation.
