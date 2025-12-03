# 📡 Satellite Communications Dataset

This folder contains the **satellite communications dataset** used for analyzing ground station observations, satellite metadata, transmitters, and telemetry.  
The dataset is structured into multiple relational tables, each serving a specific role in the ecosystem of satellites and ground stations.

---

## 📑 Overview

- **Total Tables:** 15  
- **Main Themes:**  
  - Ground stations & antennas  
  - Satellites & operators  
  - Transmitters & communication modes  
  - Telemetry decoders  
  - Observations (largest dataset)

This dataset is ideal for research in **satellite communications, orbital tracking, signal analysis, and ground station networks**.

---

## 🗂️ Schema Summary

### 1. Ground Stations & Hardware
| Table | Purpose | Key Columns |
|-------|----------|-------------|
| **base_station** | Defines ground stations (location, equipment, status) | `id`, `name`, `lat`, `lng`, `alt`, `description` |
| **base_stationstatuslog** | Logs status changes of stations over time | `id`, `status`, `changed`, `station_id` |
| **base_stationtype** | Categories of stations (only "RF" in dataset) | `id`, `name` |
| **base_antenna** | Links antennas to stations and types | `id`, `antenna_type_id`, `station_id` |
| **base_antennatype** | Catalog of antenna types | `id`, `name` |
| **base_frequencyrange** | Frequency ranges supported by antennas | `id`, `min_frequency`, `max_frequency`, `antenna_id` |

---

### 2. Satellites & Metadata
| Table | Purpose | Key Columns |
|-------|----------|-------------|
| **base_satellite** | Core satellite table linking entries & identifiers | `id`, `satellite_entry_id`, `satellite_identifier_id` |
| **base_satelliteentry** | Metadata: names, NORAD IDs, operators, status | `id`, `norad_cat_id`, `name`, `status`, `operator_id` |
| **base_satelliteidentifier** | Unique satellite identifiers (UUID‑style) | `id`, `sat_id`, `created` |
| **base_operator** | Organizations operating satellites | `id`, `name`, `website` |
| **base_launch** | Launch metadata (currently empty) | `id`, `name`, `forum_thread_url`, `created` |

---

### 3. Communications
| Table | Purpose | Key Columns |
|-------|----------|-------------|
| **base_transmitterentry** | Defines transmitters (frequencies, modes, baud rates) | `id`, `description`, `uplink_low`, `downlink_low`, `baud`, `satellite_id` |
| **base_mode** | Catalog of communication modes | `id`, `name` |
| **base_telemetry** | Telemetry decoder definitions | `id`, `name`, `decoder`, `satellite_id` |

---

### 4. Observations
| Table | Purpose | Key Columns |
|-------|----------|-------------|
| **base_observation** | Records satellite pass observations | `id`, `start`, `end`, `ground_station_id`, `sat_id`, `status`, `tle_line_1`, `tle_line_2` |

- **Row count:** 12,546,241 (largest table)  
- Contains detailed metadata about each observation, including station location, transmitter parameters, and orbital elements.

---

## 🗺️ Entity–Relationship Diagram (Schema)

---
base_operator ───< base_satelliteentry >─── base_satellite >─── base_satelliteidentifier
│ 
└───< base_transmitterentry >─── base_mode 
│ 
└───< base_telemetry

base_launch ───< base_satelliteentry

base_station ───< base_observation >─── base_satellite 
│ 
└───< base_antenna >─── base_antennatype 
│ 
└───< base_frequencyrange

base_station ───< base_stationstatuslog 
base_station ─── base_stationtype

---

### 🔑 Explanation
- **Satellites** are defined in `base_satellite`, linked to metadata (`base_satelliteentry`) and identifiers (`base_satelliteidentifier`).  
- **Operators** manage satellites via `base_satelliteentry.operator_id`.  
- **Transmitters** (`base_transmitterentry`) and **Telemetry decoders** (`base_telemetry`) are tied to satellites.  
- **Modes** (`base_mode`) describe modulation schemes used by transmitters.  
- **Stations** (`base_station`) observe satellites (`base_observation`) and host antennas (`base_antenna`).  
- **Antennas** have types (`base_antennatype`) and frequency ranges (`base_frequencyrange`).  
- **Station status logs** track operational changes over time.  
- **Station types** categorize stations (currently only "RF").  
- **Launches** (empty in dataset) would link to satellites via `base_satelliteentry.launch_id`.

---

## 📊 Relationships

- **Stations ↔ Antennas ↔ Frequency ranges**  
- **Satellites ↔ Operators ↔ Launches**  
- **Satellites ↔ Transmitters ↔ Modes**  
- **Satellites ↔ Telemetry decoders**  
- **Observations ↔ Satellites ↔ Stations**

This schema allows for complex queries such as:
- Which satellites are operated by ESA and observed by station KB9JHU?  
- What frequency ranges are supported by antennas at Hackerspace.gr?  
- Which transmitters use AFSK or BPSK modes?  
- How many observations exist for OSCAR‑7 in 2020?

---

## 🚀 Usage

You can query the dataset using SQL or load it into Python with libraries like **SQLAlchemy** and **Pandas** for analysis.  
Example:

```python
import pandas as pd

# Example: Get all satellites operated by ESA
query = """
SELECT s.id, se.name, o.name AS operator
FROM base_satellite s
JOIN base_satelliteentry se ON s.satellite_entry_id = se.id
JOIN base_operator o ON se.operator_id = o.id
WHERE o.name = 'ESA';
"""
df = pd.read_sql(query, engine)
print(df)


