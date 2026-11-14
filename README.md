# Multi-Basin Synoptic Drivers, LPS Kinematics, and Monsoon Flood Responses
## Synthesis of 3×3 Combined Unstandardized SOM Analysis for Godavari, Krishna, and Narmada Basins (1965–2025)

---

## 1. Executive Overview

This directory contains the synthesized results, synoptic atlases, spatial rainfall distributions, hydrologic hydrographs, and Low-Pressure System (LPS) trajectory rose comparisons for **Basin-Wide Monsoon High Flow Events (HFEs)** across three of India's major river basins:
- **Godavari Basin** ($312,812\text{ km}^2$) — Core Nodes: **[3, 6, 9]** (from 3×3 SOM)
- **Krishna Basin** ($258,948\text{ km}^2$) — Core Nodes: **[1, 2, 5]** (from 4×3 SOM)
- **Narmada Basin** ($98,796\text{ km}^2$) — Core Nodes: **[3, 5, 8]** (from 3×3 SOM)

The analysis integrates 61 years (1965–2025) of atmospheric reanalysis (ERA5), high-resolution gridded rainfall (IMD $0.25^\circ \times 0.25^\circ$), and long-term river discharge observations from the Central Water Commission (CWC). Spatio-temporal atmospheric patterns are classified using **Unstandardized 3×3 Self-Organizing Maps (SOM)** trained on coupled 5-day sequences of Mean Sea Level Pressure (MSLP) anomalies and vertically Integrated Vapor Transport (IVT) vectors.

---

## 2. Directory Structure & File Manifest

```
Selected_Nodes_Combined_Unstandardized_Three_Basins_Synthesis/
│
├── README.md                                                              # This comprehensive documentation
├── Three_Basins_Study_Area_and_Station_Network_Map.png                    # Multi-panel study area and station network map
├── Three_Basins_Study_Area_and_Station_Network_Map.pdf                    # Publication-grade vector PDF map
├── Three_Basins_Selected_Nodes_LPS_Circle_Extent_Resultant_Arrow_Master_1x3_White_BG.png   # Master 1x3 LPS Trajectory Comparison
├── Three_Basins_Selected_Nodes_LPS_Circle_Extent_Resultant_Arrow_Master_1x3_White_BG.pdf   # Vector PDF version
│
├── 00_Study_Area_Map/
│   ├── Three_Basins_Study_Area_and_Station_Network_Map.png
│   └── Three_Basins_Study_Area_and_Station_Network_Map.pdf
│
├── 01_LPS_Trajectory_Master_Comparison/
│   ├── Three_Basins_Selected_Nodes_LPS_Circle_Extent_Resultant_Arrow_Master_1x3_White_BG.png
│   ├── Three_Basins_Selected_Nodes_LPS_Circle_Extent_Resultant_Arrow_Master_1x3_White_BG.pdf
│   └── Three_Basins_Selected_Nodes_LPS_Circle_Extent_and_Arrow_Metrics.csv                 # Detailed kinematic metrics
│
├── 02_Master_Triplets_6x5_Figures/
│   ├── Godavari_Combined_Unstandardized_3x3_Core_Nodes_03_06_09_MSLP_Anomaly_Rainfall_Hydrographs_Master_6x5.png/.pdf
│   ├── Krishna_Combined_Unstandardized_4x3_Core_Nodes_01_02_05_MSLP_Anomaly_Rainfall_Hydrographs_Master_6x5.png/.pdf
│   └── Narmada_Combined_Unstandardized_3x3_Core_Nodes_03_05_08_MSLP_Anomaly_Rainfall_Hydrographs_Master_6x5.png/.pdf
│
├── 03_Individual_Basin_LPS_Roses/
│   ├── Godavari_Selected_Nodes_03_06_09_LPS_Circle_Extent_Resultant_Arrow_White_BG.png/.pdf
│   ├── Krishna_Selected_Nodes_01_02_05_LPS_Circle_Extent_Resultant_Arrow_White_BG.png/.pdf
│   └── Narmada_Selected_Nodes_03_05_08_LPS_Circle_Extent_Resultant_Arrow_White_BG.png/.pdf
│
└── 04_Synoptic_and_Lifecycle_Atlases/
    ├── Godavari_Combined_Unstandardized_SOM_3x5_Synoptic_Overlay_Nodes_03_06_09.png/.pdf
    ├── Godavari_Combined_Unstandardized_SOM_3x5_MSLP_Lifecycle_Nodes_03_06_09.png/.pdf
    ├── Krishna_Combined_Unstandardized_SOM_3x5_Synoptic_Overlay_Nodes_02_06_09.png/.pdf
    ├── Krishna_Combined_Unstandardized_SOM_3x5_MSLP_Lifecycle_Nodes_02_06_09.png/.pdf
    ├── Narmada_Combined_Unstandardized_SOM_3x5_Synoptic_Overlay_Nodes_03_05_08.png/.pdf
    └── Narmada_Combined_Unstandardized_SOM_3x5_MSLP_Lifecycle_Nodes_03_05_08.png/.pdf
```

---

## 3. Data Sources & Specifications

### 3.1 Atmospheric Fields (ERA5 Reanalysis)
- **Period**: 1965–2025 (61 Southwest Monsoon seasons, June to September [JJAS]).
- **Domain**: $5.0^\circ\text{–}27.5^\circ\text{N}$, $65.0^\circ\text{–}95.0^\circ\text{E}$ (South Asian Monsoon & Northern Indian Ocean Domain).
- **Spatial Resolution**: $0.25^\circ \times 0.25^\circ$ regular grid ($91 \times 121$ grid points).
- **Variables**:
  - Daily Mean Sea Level Pressure ($\text{MSLP}$ in $\text{Pa}$).
  - Vertically Integrated Eastward Water Vapor Flux ($\text{VIWVE}$ / $u_{\text{IVT}}$ in $\text{kg}\cdot\text{m}^{-1}\cdot\text{s}^{-1}$).
  - Vertically Integrated Northward Water Vapor Flux ($\text{VIWVN}$ / $v_{\text{IVT}}$ in $\text{kg}\cdot\text{m}^{-1}\cdot\text{s}^{-1}$).
  - IVT Magnitude: $|\mathbf{IVT}| = \sqrt{u_{\text{IVT}}^2 + v_{\text{IVT}}^2}$.
- **Climatology Baseline**: Day-of-year (DOY) smoothed daily climatology computed over the 61-year record (1965–2025) to isolate true transient synoptic anomalies ($\Delta\text{MSLP}$).

### 3.2 Precipitation (IMD Gridded Rainfall)
- **Source**: India Meteorological Department (IMD) daily gridded rainfall dataset.
- **Resolution**: $0.25^\circ \times 0.25^\circ$ ($79 \times 103$ grid over India).
- **Period**: 1965–2025 JJAS.
- **Rendering**: Un-interpolated discrete raster grid cells strictly bounded by basin polygons.

### 3.3 Hydrometric Observations (CWC Gauging Stations)
- **Godavari**: 14 major CWC streamflow stations (Governing terminal gauge: Tekra / Polavaram).
- **Krishna**: 18 major CWC streamflow stations (Governing terminal gauge: Keesara / Vijayawada).
- **Narmada**: 6 major CWC streamflow stations (Governing terminal gauge: Garudeshwar).
- **Thresholds**: 99th percentile of daily monsoon discharge ($Q_{99}$) established across 20+ to 60-year operational records.

---

## 4. Methodological Framework

### 4.1 Identification of Basin-Wide Monsoon High Flow Events (HFEs)
1. **Station Exceedance**: A station experiences a high-flow event when daily discharge exceeds its long-term monsoon 99th percentile threshold ($Q \ge Q_{99}$).
2. **Basin-Wide Synchronization**: Multi-station synchronous flooding is identified when multiple sub-basins exceed $Q_{99}$ within a moving temporal envelope.
3. **Day 0 Determination**: Day 0 is defined as the date of peak hydrologic discharge at the governing downstream/terminal index station of the basin (Tekra for Godavari, Keesara for Krishna, Garudeshwar for Narmada).
4. **Event Independence**: A minimum inter-event separation buffer of 5 days is enforced to prevent double-counting continuous flood hydrograph waves.

### 4.2 Synoptic Lag Window & Coupled Feature Space
For each identified basin-wide HFE, atmospheric states are sampled across a 5-day precursor-to-passage window:
$$\text{Window} = [\text{Day } -2, \, \text{Day } -1, \, \text{Day } 0, \, \text{Day } +1, \, \text{Day } +2]$$
- **Coupled Tensor**: For each event $k$, the input vector couples the 5-day fields of $\Delta\text{MSLP}(x, y, t)$ and IVT vector components $(u(x, y, t), v(x, y, t))$.
- **Unstandardized Preservation**: Retaining raw unstandardized physical units ($\text{Pa}$ and $\text{kg}\cdot\text{m}^{-1}\cdot\text{s}^{-1}$) allows the SOM to partition states based on natural physical energy gradients, distinctly separating severe cyclonic land depressions from moderate monsoon lows.

### 4.3 Self-Organizing Map (SOM) Clustering & Core Node Selection
A 2D toroidal lattice of $3 \times 3 = 9$ nodes is trained using a batch SOM algorithm with a Gaussian neighborhood decay function.
From the 9 topological nodes, three **Core Archetype Nodes** were selected per basin to capture the spectrum of flood generation:

| Basin | Selected Nodes | Primary Hydrometeorological Mechanism |
| :--- | :---: | :--- |
| **Godavari** | **[3, 6, 9]** | Deep Bay of Bengal Monsoon Depressions tracking WNW across the central rift axis into northern Telangana and Maharashtra. |
| **Krishna** | **[2, 6, 9]** | Transition from southern peninsular Arabian Sea surges (Node 2) to deep continental monsoon lows (Node 6) and intense Bay depressions traversing the upper Bhima/Tungabhadra catchments (Node 9). |
| **Narmada** | **[3, 5, 8]** | Linear east-to-west tracking depressions channeled along the Satpura-Vindhya rift corridor, from upstream inception (Node 5) to central basin stall (Node 8) and deepest overland depression (Node 3). |

### 4.4 Antecedent Moisture & Hydrograph Ensemble Decomposition
- **7-Day Antecedent Precipitation**: Accumulated catchment rainfall over the precursor window $[\text{Day } -8, \text{Day } -2]$:
  $$P_{\text{ant}, 7\text{d}} = \sum_{d=-8}^{-2} P(d)$$
- **Condition Stratification**:
  - **Wet Antecedent**: $P_{\text{ant}, 7\text{d}} \ge P_{95}$ (catchment soil storage saturated prior to storm arrival).
  - **Dry Antecedent**: $P_{\text{ant}, 7\text{d}} < P_{95}$ (catchment possesses unsaturated soil moisture deficit).
- **Hydrograph Compositing**: Ensembles display the median/mean hydrograph trajectory alongside the $\pm 1\sigma$ inter-event spread and station $Q_{99}$ threshold line.

### 4.5 LPS Kinematic Tracking & Trajectory Rose Analysis
To quantify the kinematics of Low-Pressure Systems generating each flood archetype:
1. **Center Tracking**: The depression center $(x_c, y_c)$ for each day $t \in [-2, +2]$ is located at the local minimum of the composite MSLP anomaly field:
   $$(x_c, y_c)_t = \arg\min_{(x, y)} \Delta\text{MSLP}(x, y, t)$$
2. **Day of Maximum Intensity ($t_{\text{peak}}$)**:
   $$t_{\text{peak}} = \arg\min_{t \in [-2, +2]} \left[\min_{(x, y)} \Delta\text{MSLP}(x, y, t)\right]$$
3. **Extent Radius ($R$)**: The spatial extent is measured as the equivalent circular radius ($R = \sqrt{A/\pi}$) of the closed $-200\text{ Pa}$ negative MSLP anomaly contour at $t_{\text{peak}}$, capturing the effective isobaric circulation footprint.
4. **Resultant Direction & Displacement**: The kinematic trajectory is calculated as the resultant displacement vector from the storm center at $t_{\text{peak}}$ to its position on **Day +2**:
   $$\mathbf{D}_{\text{resultant}} = (x_c, y_c)_{\text{Day }+2} - (x_c, y_c)_{t_{\text{peak}}}$$
5. **Physical Trajectory Rose Rendering**:
   - **Origin**: Center of the polar rose represents the storm position on the Day of Maximum Intensity.
   - **Solid Arrows**: Solid light-filled arrows with crisp boundaries indicating resultant direction and total travel distance.
   - **Arrow Width**: Proportional to peak storm intensity ($|\Delta\text{MSLP}_{\text{peak}}|$ in $\text{Pa}$).
   - **Deflection Arc**: Solid color arc measuring the angular deviation from the **West Axis** ($0^\circ = \text{Due West}$, positive counter-clockwise/north of west).
   - **Length Scale**: Physical coordinate scaling calibrated to $1\text{ cm} = 200\text{ km}$.
   - **Extent Circle**: Outer circle delineates the storm extent radius ($R$) of the most expansive node.

---

## 5. Quantitative Synthesis of Selected Core Nodes

The table below synthesizes the kinematic and synoptic metrics computed for each selected archetype node across the three basins:

| Basin | Node | Events ($N$) | Peak Intensity Day | Peak MSLP Anomaly ($\text{Pa}$) | Extent Radius ($R$, $\text{km}$) | Resultant Direction | Angle from West ($\theta$) | Resultant Displacement ($\text{km}$) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Godavari** | **Node 3** | $11$ | Day $-1$ | $-694.5$ | $1,386.9$ | **WNW** ($286.2^\circ$) | **$16.2^\circ$** | $1,490.1$ |
| **Godavari** | **Node 6** | $14$ | Day $-1$ | **$-895.1$** | $1,031.2$ | **WNW** ($292.1^\circ$) | **$22.1^\circ$** | $1,474.5$ |
| **Godavari** | **Node 9** | $12$ | Day $-1$ | $-535.6$ | $748.9$ | **WNW** ($284.2^\circ$) | **$14.2^\circ$** | $1,471.0$ |
| **Krishna** | **Node 1** | $13$ | Day $+1$ | $-580.7$ | $1,110.5$ | **WNW** ($294.0^\circ$) | **$24.0^\circ$** | $341.6$ |
| **Krishna** | **Node 2** | $8$ | Day $+1$ | **$-706.0$** | $1,281.8$ | **W** ($262.4^\circ$) | **$-7.6^\circ$** | $419.6$ |
| **Krishna** | **Node 5** | $6$ | Day $-1$ | $-561.9$ | $1,064.6$ | **WNW** ($290.9^\circ$) | **$20.9^\circ$** | $1,557.8$ |
| **Narmada** | **Node 3** | $6$ | Day $0$ | **$-660.2$** | $990.9$ | **WNW** ($282.8^\circ$) | **$12.8^\circ$** | $624.6$ |
| **Narmada** | **Node 5** | $7$ | Day $-2$ | $-511.9$ | $579.5$ | **NW** ($308.1^\circ$) | **$38.1^\circ$** | $900.0$ |
| **Narmada** | **Node 8** | $9$ | Day $-1$ | $-506.4$ | $484.5$ | **NW** ($311.7^\circ$) | **$41.7^\circ$** | $876.4$ |

---

## 6. Key Comparative Insights Across Basins

### 6.1 Godavari Basin: The Monsoonal Depression Highway
- **Kinematic Coherence**: Across all three nodes (3, 6, 9), storm tracks exhibit extraordinary directionality ($284^\circ\text{–}292^\circ$, or $14^\circ\text{–}22^\circ$ north of west) and sustained westward translational velocity ($\approx 1,470\text{–}1,490\text{ km}$ displacement over 3 days).
- **Extreme Depression Core**: **Node 6** represents the most intense synoptic depression identified across all three basins ($-895.1\text{ Pa}$ central anomaly at Day $-1$), generating widespread rainfall exceeding $100\text{ mm/day}$ over the Wainganga and Indravati catchments and triggering devastating downstream flood peaks at Tekra and Polavaram.
- **Massive Spatial Footprint**: Extent radius exceeds $1,380\text{ km}$ in Node 3, covering virtually the entire northern and central peninsular sub-continent.

### 6.2 Krishna Basin: Bimodal Bay vs. Arabian Sea Dynamics (4×3 SOM)
- **Synoptic Diversity Across 12 Topology States**: The refined 4×3 SOM delineates three distinct archetypal mechanisms:
  1. **Head Bay Monsoon Depression (Node 1)**: Forms over the Head Bay of Bengal, peaks on Day $+1$ ($-580.7\text{ Pa}$, $R = 1,110.5\text{ km}$), and tracks inland WNW ($294.0^\circ$, $\theta = 24.0^\circ$) across Telangana and coastal Andhra Pradesh.
  2. **Deep Inland Peninsular Low (Node 2)**: An exceptionally deep, mature inland vortex ($-706.0\text{ Pa}$, $R = 1,281.8\text{ km}$) centered right over the middle and upper Krishna catchment ($19.5^\circ\text{N}, 79.25^\circ\text{E}$), propagating nearly due West ($262.4^\circ$, $\theta = -7.6^\circ$ south of West), driving basin-wide concurrent flood crests.
  3. **Offshore Arabian Sea Cyclonic Shear Vortex (Node 5)**: Develops off the Konkan/Goa coast, peaks early on Day $-1$ ($-561.9\text{ Pa}$, $R = 1,064.6\text{ km}$), and channels intense low-level westerly monsoon moisture directly onto the Western Ghats barrier ($1,557.8\text{ km}$ displacement, $\theta = 20.9^\circ$), precipitating heavy headwater runoff 24–48 hours ahead of downstream discharge peaks.

### 6.3 Narmada Basin: Topographic Channelling Along the Rift Corridor
- **East-West Channelling**: All Narmada storm vectors are tightly bound between $282^\circ$ and $312^\circ$ azimuths. The Satpura and Vindhya mountain ranges act as a natural orographic flume, guiding Bay-born land depressions westward towards the Gulf of Khambhat.
- **Stalling vs. Progressive Inception**:
  - **Node 3**: Represents a stationary or slow-moving mature depression ($-660.2\text{ Pa}$) that reaches maximum intensity on Day 0 right over the middle Narmada basin (Hoshangabad/Sandia), yielding extreme local runoff before moving towards the estuary ($624.6\text{ km}$ travel).
  - **Nodes 5 & 8**: Feature storms that develop early (Day $-2$ / Day $-1$) over the Odisha/Chhota Nagpur coast and sweep the entire length of the Narmada valley ($876\text{–}900\text{ km}$ travel).

---

## 7. Figure Descriptions

### 7.1 Master Triplet 6×5 Figures (`02_Master_Triplets_6x5_Figures/`)
Each figure features a compact $6 \times 5$ multi-perspective matrix:
- **Rows 1, 3, 5 (Atmospheric Lifecycle)**: 5 columns representing precursor-to-passage evolution ($\text{Day } -2$ to $\text{Day } +2$) showing MSLP anomaly shading (blue = negative depression, red = positive ridge), isobars, and IVT moisture flux quivers.
- **Rows 2, 4, 6, Column 0 (Spatial Rainfall Grid)**: Un-interpolated $0.25^\circ \times 0.25^\circ$ IMD rainfall raster strictly clipped to the basin watershed divide, overlaid with river networks and 4 prominent numbered red station badges.
- **Rows 2, 4, 6, Columns 1–4 (Station Hydrographs)**: Dual antecedent hyetographs (top inverted bars) and hydrographs (bottom hydrograph curves with $\pm 1\sigma$ envelopes) for the top 4 participating stations, benchmarked against station $Q_{99}$ thresholds.

### 7.2 LPS Trajectory Master 1×3 Comparison (`01_LPS_Trajectory_Master_Comparison/`)
A unified side-by-side comparison figure placing Godavari, Krishna, and Narmada trajectory roses on an identical coordinate grid ($-1,850\text{ km}$ to $+1,850\text{ km}$):
- Facilitates direct visual comparison of storm intensity (arrow thickness), reach (extent circle radius), travel speed (arrow length), and directional variance (angle arcs from West).

### 7.3 Study Area & Station Network Map (`00_Study_Area_Map/`)
A publication-quality geographic overview map titled **"Study Area"**:
- **Unified Indian Context**: Shows all three river basins (Narmada, Godavari, and Krishna) inside the natural high-resolution map of India (Natural Earth 10m physical coastline, authentic borders, and subtle state boundaries).
- **Drainage & Gauging Network**: Illustrates the internal Order-3+ river drainage network and the geographic distribution of all $N=38$ Central Water Commission (CWC) streamflow gauging stations across the upper, middle, and lower reaches.
- **Inside Legend**: Clean, self-contained inside legend showing distinct thematic colors for the three river basins alongside the CWC gauging station markers.

---
*Generated as part of the Comprehensive Monsoon High Flow Event (HFE) & SOM Coupling Research Program (1965–2025).*
