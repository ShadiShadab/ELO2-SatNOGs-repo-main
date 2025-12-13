# 📊 SatNOGS Dataset Schema Summary

## Table: base_antenna
- Row count: 4437
- Columns: id, antenna_type_id, station_id

### Preview (first 5 rows)
|   id |   antenna_type_id |   station_id |
|-----:|------------------:|-------------:|
|    1 |                12 |          256 |
|    2 |                12 |         1536 |
|    7 |                10 |          771 |
|    8 |                13 |         1285 |
|    9 |                15 |            6 |

---

## Table: base_antennatype
- Row count: 17
- Columns: id, name

### Preview (first 5 rows)
|   id | name         |
|-----:|:-------------|
|    6 | Cross Yagi   |
|    1 | Dipole       |
|    3 | Discone      |
|   12 | Eggbeater    |
|    4 | Ground Plane |

---

## Table: base_frequencyrange
- Row count: 5311
- Columns: id, min_frequency, max_frequency, antenna_id

### Preview (first 5 rows)
|   id |   min_frequency |   max_frequency |   antenna_id |
|-----:|----------------:|----------------:|-------------:|
|    1 |        1.35e+08 |        1.48e+08 |            1 |
|    2 |        4.3e+08  |        4.4e+08  |            2 |
|    7 |        1.35e+08 |        1.48e+08 |            7 |
|    8 |        4.3e+08  |        4.4e+08  |            8 |
|    9 |        4e+08    |        4.7e+08  |            9 |

---

## Table: base_launch
- Row count: 0
- Columns: id, name, forum_thread_url, created, created_by_id

### Preview (first 5 rows)
| id   | name   | forum_thread_url   | created   | created_by_id   |
|------|--------|--------------------|-----------|-----------------|

---

## Table: base_mode
- Row count: 56
- Columns: id, name

### Preview (first 5 rows)
|   id | name         |
|-----:|:-------------|
|   90 | 4FSK         |
|   49 | AFSK         |
|   78 | AFSK TUBiX10 |
|   17 | AHRPT        |
|   19 | AM           |

---

## Table: base_observation
- Row count: 12546241
- Columns: id, start, end, author_id, ground_station_id, max_altitude, rise_azimuth, set_azimuth, waterfall_status_datetime, vetted_status, waterfall_status_user_id, archive_identifier, archive_url, archived, experimental, client_metadata, client_version, transmitter_baud, transmitter_created, transmitter_description, transmitter_downlink_drift, transmitter_downlink_high, transmitter_downlink_low, transmitter_invert, transmitter_type, transmitter_uplink_drift, transmitter_uplink_high, transmitter_uplink_low, transmitter_uuid, transmitter_mode, status, waterfall_status, tle_line_0, tle_line_1, tle_line_2, tle_source, tle_updated, station_alt, station_antennas, station_lat, station_lng, audio_zipped, payload, waterfall, center_frequency, transmitter_status, transmitter_unconfirmed, sat_id

### Preview (first 5 rows)
|   id | start               | end                 |   author_id |   ground_station_id | max_altitude   | rise_azimuth   | set_azimuth   | waterfall_status_datetime   | vetted_status   |   waterfall_status_user_id | archive_identifier                       | archive_url                                                                                                                                           |   archived |   experimental | client_metadata   | client_version   |   transmitter_baud | transmitter_created        | transmitter_description         | transmitter_downlink_drift   | transmitter_downlink_high   |   transmitter_downlink_low |   transmitter_invert | transmitter_type   | transmitter_uplink_drift   | transmitter_uplink_high   |   transmitter_uplink_low | transmitter_uuid       | transmitter_mode   |   status | waterfall_status   | tle_line_0   | tle_line_1   | tle_line_2   | tle_source   | tle_updated   | station_alt   | station_antennas   | station_lat   | station_lng   |   audio_zipped | payload   | waterfall   | center_frequency   | transmitter_status   | transmitter_unconfirmed   | sat_id                   |
|-----:|:--------------------|:--------------------|------------:|--------------------:|:---------------|:---------------|:--------------|:----------------------------|:----------------|---------------------------:|:-----------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------|-----------:|---------------:|:------------------|:-----------------|-------------------:|:---------------------------|:--------------------------------|:-----------------------------|:----------------------------|---------------------------:|---------------------:|:-------------------|:---------------------------|:--------------------------|-------------------------:|:-----------------------|:-------------------|---------:|:-------------------|:-------------|:-------------|:-------------|:-------------|:--------------|:--------------|:-------------------|:--------------|:--------------|---------------:|:----------|:------------|:-------------------|:---------------------|:--------------------------|:-------------------------|
|   23 | 2015-10-12 15:13:16 | 2015-10-12 15:20:01 |         165 |                   2 |                |                |               | 2017-05-26 08:04:08         | bad             |                        172 | satnogs-observations-000000001-000010000 | https://archive.org/download/satnogs-observations-000000001-000010000/satnogs-observations-000000001-000001000.zip/satnogs_23_2015-10-12T15-20-01.ogg |          1 |              0 |                   |                  |                nan | 2019-04-18 05:39:53.343316 | CW Beacon (F2A)                 |                              |                             |                  435948500 |                    0 | Transmitter        |                            |                           |            nan           | MZgyEeYrdJsLnHCt3je6Ed | FM                 |     -100 |                    |              |              |              |              |               |               |                    |               |               |              1 |           |             |                    |                      |                           | UTXU-4881-3195-9394-3367 |
|   25 | 2015-10-12 17:03:08 | 2015-10-12 17:15:37 |         165 |                   2 |                |                |               | 2017-05-26 08:18:15         | bad             |                        172 | satnogs-observations-000000001-000010000 | https://archive.org/download/satnogs-observations-000000001-000010000/satnogs-observations-000000001-000001000.zip/satnogs_25_2015-10-12T17-15-37.ogg |          1 |              0 |                   |                  |                nan | 2019-04-18 05:39:53.343316 | CW TLM                          |                              |                             |                  437485000 |                    0 | Transmitter        |                            |                           |            nan           | xfcdPcSWKbqzRDxZZ79yhX | CW                 |     -100 |                    |              |              |              |              |               |               |                    |               |               |              1 |           |             |                    |                      |                           | FVYN-9469-5031-2236-7972 |
|   27 | 2015-10-12 17:30:27 | 2015-10-12 17:43:51 |         165 |                   2 |                |                |               | 2017-05-26 08:22:41         | bad             |                        172 | satnogs-observations-000000001-000010000 | https://archive.org/download/satnogs-observations-000000001-000010000/satnogs-observations-000000001-000001000.zip/satnogs_27_2015-10-12T17-43-51.ogg |          1 |              0 |                   |                  |               1200 | 2019-04-18 05:39:53.343316 | AFSK 1200                       |                              |                             |                  437438300 |                    1 | Transceiver        |                            |                           |              4.37438e+08 | MTMEfksHRarmn9mxBJuEF4 | AFSK               |     -100 |                    |              |              |              |              |               |               |                    |               |               |              1 |           |             |                    |                      |                           | HXCH-9043-9893-2952-4877 |
|   28 | 2015-10-12 18:08:16 | 2015-10-12 18:21:54 |         165 |                   2 |                |                |               | 2017-07-22 11:14:03         | bad             |                        180 | satnogs-observations-000000001-000010000 | https://archive.org/download/satnogs-observations-000000001-000010000/satnogs-observations-000000001-000001000.zip/satnogs_28_2015-10-12T18-21-54.ogg |          1 |              0 |                   |                  |                  0 | 2019-04-18 05:39:53.343316 | Mode V/U FM Voice CTCSS 67.0 Hz |                              |                             |                  436795000 |                    0 | Transceiver        |                            |                           |              1.4585e+08  | Y9P45XRJH8yAsbDDe4qHnE | FM                 |     -100 |                    |              |              |              |              |               |               |                    |               |               |              1 |           |             |                    |                      |                           | IRES-5964-9687-1982-0089 |
|   33 | 2015-10-13 17:08:24 | 2015-10-13 17:21:56 |         165 |                   2 |                |                |               | 2017-09-10 19:00:05         | bad             |                        180 | satnogs-observations-000000001-000010000 | https://archive.org/download/satnogs-observations-000000001-000010000/satnogs-observations-000000001-000001000.zip/satnogs_33_2015-10-13T17-21-56.ogg |          1 |              0 |                   |                  |                nan | 2019-04-18 05:39:53.343316 | CW Beacon                       |                              |                             |                  437250000 |                    0 | Transmitter        |                            |                           |            nan           | ecmM575wCsfnP4UyZPLnoP | CW                 |     -100 |                    |              |              |              |              |               |               |                    |               |               |              1 |           |             |                    |                      |                           | ZRIM-9073-8711-5268-6171 |

---

## Table: base_operator
- Row count: 6
- Columns: id, name, names, description, website

### Preview (first 5 rows)
|   id | name   | names                                                     | description                                                                                                               | website                      |
|-----:|:-------|:----------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------|:-----------------------------|
|    1 | UVG    | Universidad del Valle de Guatemala                        |                                                                                                                           | https://www.uvg.edu.gt/      |
|    2 | LSF    | Libre Space Foundation                                    |                                                                                                                           | https://libre.space          |
|    3 | ESA    | European Space Agency                                     |                                                                                                                           | https://www.esa.int/         |
|    4 | ISRO   | Indian Space Research Organisation                        | The Indian Space Research Organisation is the national space agency of the Republic of India, headquartered in Bengaluru. | https://www.isro.gov.in/     |
|    5 | CIOMP  | Changchun Institute of Optics, Fine Mechanics and Physics |                                                                                                                           | http://english.ciomp.cas.cn/ |

---

## Table: base_satellite
- Row count: 2903
- Columns: id, last_modified, associated_satellite_id, satellite_entry_id, satellite_identifier_id

### Preview (first 5 rows)
|   id | last_modified              | associated_satellite_id   |   satellite_entry_id |   satellite_identifier_id |
|-----:|:---------------------------|:--------------------------|---------------------:|--------------------------:|
|    1 | 2021-07-21 10:11:41.947596 |                           |                 7538 |                         1 |
|    2 | 2021-07-21 10:11:41.949944 |                           |                 1843 |                         2 |
|    3 | 2021-07-21 10:11:41.951757 |                           |                 1836 |                         3 |
|    4 | 2021-07-21 10:11:41.953531 |                           |                 1930 |                         4 |
|    5 | 2021-07-21 10:11:41.955319 |                           |                 1835 |                         5 |

---

## Table: base_satelliteentry
- Row count: 9759
- Columns: id, norad_cat_id, name, image, names, status, description, decayed, dashboard_url, countries, deployed, launched, website, operator_id, norad_follow_id, approved, citation, created, created_by_id, reviewed, reviewer_id, satellite_identifier_id, launch_id, receive_review_update, review_message

### Preview (first 5 rows)
|   id |   norad_cat_id | name        | image                             | names     | status   | description                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | decayed   | dashboard_url   | countries   | deployed   | launched   | website   | operator_id   | norad_follow_id   |   approved | citation                                | created                    | created_by_id   | reviewed                   | reviewer_id   |   satellite_identifier_id | launch_id   |   receive_review_update | review_message   |
|-----:|---------------:|:------------|:----------------------------------|:----------|:---------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------|:----------------|:------------|:-----------|:-----------|:----------|:--------------|:------------------|-----------:|:----------------------------------------|:---------------------------|:----------------|:---------------------------|:--------------|--------------------------:|:------------|------------------------:|:-----------------|
|    1 |           7530 | OSCAR 7     | satellites/AO-7-Model-300x180.gif | AO-7      | alive    | This satellite was a small communications satellite designed by amateur radio operators. Attitude control was accomplished with a magnetic and damping rods. There were two beacon experiments (near 30 and 430 MHz), and two repeaters with code storage capability. The repeater receiver frequencies were near 146 and 432 MHz, and the transmitter frequencies near 30 and 146 MHz. The command system was manufactured in Australia and the second repeater in Germany. |           |                 |             |            |            |           |               |                   |          1 | CITATION NEEDED - https://xkcd.com/285/ | 2021-07-21 10:11:41.973567 |                 | 2021-07-21 10:11:41.973567 |               |                        16 |             |                       0 |                  |
|    2 |          14781 | UOSAT 2     | satellites/UoSat-2.jpg            | UO-11     | alive    | Also known as OSCAR 11, this British built satellite from the University of Surrey has reached the end of it's servicable life. It still transmits telemetary based when in direct sunlight and with its watchdog timer operational. This satellite was used for communications as part of a polar expedition in 1988.                                                                                                                                                       |           |                 |             |            |            |           |               |                   |          1 | CITATION NEEDED - https://xkcd.com/285/ | 2021-07-21 10:11:41.977018 |                 | 2021-07-21 10:11:41.977018 |               |                        18 |             |                       0 |                  |
|      |                |             |                                   |  OSCAR-11 |          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |           |                 |             |            |            |           |               |                   |            |                                         |                            |                 |                            |               |                           |             |                         |                  |
|    3 |          20442 | LUSAT       | satellites/LUSAT-1.gif            | LO-19     | alive    | Lusat was launched by the same Ariane vehicle that launched SPOT-2 from the Kourou Space Center in French Guiana. It was an AMSAT amateur radio satellite. It carried a CCD camera for earth photography.                                                                                                                                                                                                                                                                    |           |                 |             |            |            |           |               |                   |          1 | CITATION NEEDED - https://xkcd.com/285/ | 2021-07-21 10:11:41.982120 |                 | 2021-07-21 10:11:41.982120 |               |                        21 |             |                       0 |                  |
|    4 |          22826 | ITAMSAT     | satellites/itamsat_1.jpg          | IO-26     | alive    | Italy's first amateur radio satellite that uses a store and repeat function to relay messages. Similar to LUSAT                                                                                                                                                                                                                                                                                                                                                              |           |                 |             |            |            |           |               |                   |          1 | CITATION NEEDED - https://xkcd.com/285/ | 2021-07-21 10:11:41.985554 |                 | 2021-07-21 10:11:41.985554 |               |                        23 |             |                       0 |                  |
|    5 |          23439 | RADIO ROSTO | satellites/radio-rosto__1.jpg     | RS-15     | alive    | Also known as RS 15. Built by a group of radio amateurs from Russia. This satellite was designed to be used as part of a high pwer constellatoin of radio M spacecraft that were eventually shelved.                                                                                                                                                                                                                                                                         |           |                 |             |            |            |           |               |                   |          1 | CITATION NEEDED - https://xkcd.com/285/ | 2021-07-21 10:11:41.987219 |                 | 2021-07-21 10:11:41.987219 |               |                        24 |             |                       0 |                  |

---

## Table: base_satelliteidentifier
- Row count: 2920
- Columns: id, sat_id, created

### Preview (first 5 rows)
|   id | sat_id                   | created                    |
|-----:|:-------------------------|:---------------------------|
|    1 | SCHX-0895-2361-9925-0309 | 2021-07-21 10:11:41.945257 |
|    2 | AMOM-6643-5608-9156-4431 | 2021-07-21 10:11:41.948554 |
|    3 | KEFJ-8497-6394-9368-1937 | 2021-07-21 10:11:41.950438 |
|    4 | FBFQ-2056-7966-4855-0749 | 2021-07-21 10:11:41.952251 |
|    5 | BIRW-7828-0822-0647-1194 | 2021-07-21 10:11:41.954037 |

---

## Table: base_station
- Row count: 3912
- Columns: id, name, image, alt, lat, lng, featured_date, owner_id, created, qthlocator, last_seen, horizon, description, status, testing, client_version, target_utilization, violator_scheduling, client_id, active_configuration_changed

### Preview (first 5 rows)
|   id | name             | image                                                               |   alt |    lat |      lng | featured_date   |   owner_id | created             | qthlocator   | last_seen           |   horizon | description                                                                                                                                                                                                          |   status |   testing | client_version         |   target_utilization |   violator_scheduling | client_id   | active_configuration_changed   |
|-----:|:-----------------|:--------------------------------------------------------------------|------:|-------:|---------:|:----------------|-----------:|:--------------------|:-------------|:--------------------|----------:|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------:|----------:|:-----------------------|---------------------:|----------------------:|:------------|:-------------------------------|
|    1 | Hackerspace.gr 1 | ground_stations/269750681_642106180166521_5486265361356106346_n.jpg |   104 | 38.017 |  23.7314 | 2015-10-11      |        848 | 2015-07-22 13:26:49 | KM18ua       | 2022-10-05 12:49:26 |        40 | Yaesu 5500, usrp b200, 2x X-Quad  Antenna 432 MHz, Power splitter, LNA (https://gitlab.com/rf-modules/rf-low-noise-amplifier), RF-Switch (https://gitlab.com/rf-modules/rf-modules), RF Power Amplifier (RA07H4047M) |        0 |         1 | 1.6                    |                  100 |                     1 |             |                                |
|    2 | KB9JHU           | ground_stations/kb9jhu_P52k3jV.png                                  |   280 | 39.236 | -86.305  | 2017-07-11      |        165 | 2015-07-22 14:24:10 | EM69uf       | 2025-07-29 22:39:46 |         5 | Yaesu G-5500 with M2 cross yagi antennas and S-band parabolic dish                                                                                                                                                   |        0 |         0 | 1.8.1                  |                  100 |                     0 |             |                                |
|      |                  |                                                                     |       |        |          |                 |            |                     |              |                     |           |                                                                                                                                                                                                                      |          |           |                        |                      |                       |             |                                |
|      |                  |                                                                     |       |        |          |                 |            |                     |              |                     |           | NOTE: S-band temporarily offline                                                                                                                                                                                     |          |           |                        |                      |                       |             |                                |
|    4 | SV1IYO           |                                                                     |   150 | 38.024 |  23.733  |                 |        168 | 2015-10-11 13:59:38 | KM18ua       | 2024-12-24 09:37:11 |         0 |                                                                                                                                                                                                                      |        0 |         1 | 1.9.2+0.g4da08be.dirty |                  100 |                     1 |             |                                |
|    5 | oe6xug           | ground_stations/oe6xug.jpg                                          |   330 | 47.059 |  15.46   |                 |        170 | 2015-11-23 12:12:51 | JN77rb       | 2025-03-24 10:09:13 |         0 | 2025-02-11: back in business triggered by fram2ham                                                                                                                                                                   |        0 |         1 | 1.0                    |                    0 |                     0 |             |                                |
|      |                  |                                                                     |       |        |          |                 |            |                     |              |                     |           | 2019-12-19: Rotor soon back, Controller replacement                                                                                                                                                                  |          |           |                        |                      |                       |             |                                |
|      |                  |                                                                     |       |        |          |                 |            |                     |              |                     |           | 2018-04-05: currently offline because of rotor failure                                                                                                                                                               |          |           |                        |                      |                       |             |                                |
|    6 | Apomahon         |                                                                     |   104 | 38.048 |  23.739  | 2016-04-25      |        172 | 2016-01-17 19:28:26 | KM18ub       | 2025-11-10 09:53:03 |        20 | Patch 435 MHz , RTL-SDR V3                                                                                                                                                                                           |        2 |         0 | 1.8.1                  |                  100 |                     0 |             |                                |

---

## Table: base_stationstatuslog
- Row count: 298893
- Columns: id, status, changed, station_id

### Preview (first 5 rows)
|   id |   status | changed             |   station_id |
|-----:|---------:|:--------------------|-------------:|
|    1 |        2 | 2018-04-02 13:55:58 |            6 |
|    3 |        2 | 2018-04-02 13:55:58 |           12 |
|    4 |        2 | 2018-04-02 13:55:58 |           13 |
|    5 |        2 | 2018-04-02 13:55:58 |           15 |
|    6 |        2 | 2018-04-02 13:55:58 |           16 |

---

## Table: base_stationtype
- Row count: 1
- Columns: id, name

### Preview (first 5 rows)
|   id | name   |
|-----:|:-------|
|    1 | RF     |

---

## Table: base_telemetry
- Row count: 185
- Columns: id, name, decoder, satellite_id

### Preview (first 5 rows)
|   id | name               | decoder   |   satellite_id |
|-----:|:-------------------|:----------|---------------:|
|    1 | ISS AX.25          | iss       |             28 |
|    2 | STRAND-1 Telemetry | strand    |             87 |
|    3 | UNISAT-6 Telemetry | us6       |            132 |
|    4 | FOX-1A Telemetry   | fox       |            178 |
|    5 | QBEE Telemetry     | qbee      |            227 |

---

## Table: base_transmitterentry
- Row count: 9869
- Columns: id, uuid, description, uplink_low, uplink_high, downlink_low, downlink_high, invert, baud, approved, downlink_mode_id, downlink_drift, type, uplink_drift, citation, created, status, created_by_id, service, uplink_mode_id, reviewed, reviewer_id, satellite_id, iaru_coordination, iaru_coordination_url, itu_notification, unconfirmed, receive_review_update, review_message

### Preview (first 5 rows)
|   id | uuid                   | description               |   uplink_low | uplink_high   |   downlink_low | downlink_high   |   invert |   baud |   approved |   downlink_mode_id |   downlink_drift | type        | uplink_drift   | citation                                | created                    | status   | created_by_id   | service   |   uplink_mode_id | reviewed                   | reviewer_id   |   satellite_id | iaru_coordination   | iaru_coordination_url   | itu_notification   |   unconfirmed |   receive_review_update | review_message   |
|-----:|:-----------------------|:--------------------------|-------------:|:--------------|---------------:|:----------------|---------:|-------:|-----------:|-------------------:|-----------------:|:------------|:---------------|:----------------------------------------|:---------------------------|:---------|:----------------|:----------|-----------------:|:---------------------------|:--------------|---------------:|:--------------------|:------------------------|:-------------------|--------------:|------------------------:|:-----------------|
|    1 | ZAKErADdWKpMiDjvKKhmmB | Mode U TLM                | nan          |               |      437125000 |                 |        0 |     12 |          1 |                  6 |              nan | Transmitter |                | CITATION NEEDED - https://xkcd.com/285/ | 2019-04-18 05:39:53.343316 | active   |                 | Unknown   |              nan | 2019-04-18 05:39:53.343316 |               |             21 | N/A                 |                         | {"urls": []}       |             0 |                       0 |                  |
|    3 | ybJ86zjXzQxDReZ5skY56B | Mode H TLM                | nan          |               |       29352000 |                 |        0 |      0 |          1 |                  6 |              nan | Transmitter |                | CITATION NEEDED - https://xkcd.com/285/ | 2019-04-18 05:39:53.343316 | active   |                 | Unknown   |              nan | 2019-04-18 05:39:53.343316 |               |             24 | N/A                 |                         | {"urls": []}       |             0 |                       0 |                  |
|    5 | Zqa2ebzyRRBffvwkLnjTVc | Mode U CW Beacon          | nan          |               |      435795000 |                 |        0 |      0 |          1 |                  6 |             1147 | Transmitter |                | CITATION NEEDED - https://xkcd.com/285/ | 2019-04-18 05:39:53.343316 | active   |                 | Unknown   |              nan | 2019-04-18 05:39:53.343316 |               |             25 | N/A                 |                         | {"urls": []}       |             0 |                       0 |                  |
|    6 | c4T33yxNiE8EAEc7V6LMQk | Mode V/U APRS,BBS 9K6 FSK |   1.4593e+08 |               |      435225000 |                 |        1 |   9600 |          1 |                 72 |              nan | Transceiver |                | CITATION NEEDED - https://xkcd.com/285/ | 2019-04-18 05:39:53.343316 | active   |                 | Unknown   |               72 | 2019-04-18 05:39:53.343316 |               |             27 | N/A                 |                         | {"urls": []}       |             0 |                       0 |                  |
|    7 | maYGaaMWsSBeDDDMpcM9ES | Mode V/U BBS1 9K6 FSK     |   1.4585e+08 |               |      435225000 |                 |        1 |   9600 |          1 |                 72 |              nan | Transceiver |                | CITATION NEEDED - https://xkcd.com/285/ | 2019-04-18 05:39:53.343316 | active   |                 | Unknown   |               72 | 2019-04-18 05:39:53.343316 |               |             27 | N/A                 |                         | {"urls": []}       |             0 |                       0 |                  |

---

