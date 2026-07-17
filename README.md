# Arctic Sea Ice Area and Ocean Mean Albedo Trend Analysis (2000–2025)

## Overview

This project analyzes long-term changes in **Arctic Sea Ice Area** and **Ocean Mean Albedo** from **2000 to 2025** using NSIDC Arctic Sea Ice raster datasets.

Unlike conventional approaches that assume a constant pixel area (625 km²), this study computes the **true geodesic area of every raster pixel** using the raster geotransform and the **WGS84 ellipsoid**, providing more physically accurate sea ice area estimates.

The project also investigates the relationship between Sea Ice Area and Ocean Mean Albedo using statistical analyses including Pearson Correlation, Mann–Kendall Trend Test, and Sen's Slope Estimator.

---

# Study Region

- Arctic Ocean
- Latitude: **60°N – 90°N**

---

# Study Period

- **2000 – 2025**
- Months analyzed:
  - March
  - April
  - May
  - June
  - July
  - August
  - September

Total Images Processed:

```
26 Years × 7 Months = 182 Raster Images
```

---

# Dataset

Source:

**NSIDC Arctic Sea Ice Raster Dataset**

Raster Information

| Parameter | Value |
|-----------|-------|
| Projection | EPSG:3411 |
| Resolution | 25 km × 25 km |
| Image Size | 304 × 448 pixels |
| Data Type | uint8 |

Pixel Classification

| Pixel Value | Class |
|-------------|-------|
| 0 | Ocean |
| 1 | Sea Ice |
| 253 | Coast |
| 254 | Land |
| 255 | Outside Study Area (Applied after Latitude Mask) |

---

# Methodology

The complete workflow followed in this project is shown below.

```
NSIDC Arctic Sea Ice Raster Images
            │
            ▼
Quality Check
            │
            ▼
Latitude Mask (60°N–90°N)
            │
            ▼
Pixel Classification
(Ocean / Sea Ice / Coast / Land)
            │
            ▼
Create Geodesic Pixel Area Grid
(using raster transform + WGS84 ellipsoid)
            │
            ▼
Assign an individual area
to every pixel
            │
            ▼
Sea Ice Area
=
Sum of all geodesic areas
classified as Sea Ice
            │
            ▼
Convert to Million km²
            │
            ▼
Annual Statistics
            │
            ▼
Correlation Analysis
            │
            ▼
Trend Analysis
            │
            ▼
Visualization
```

---

# Geodesic Pixel Area Calculation

Instead of assuming that every raster pixel represents exactly **625 km²**, this project computes the actual area of every pixel individually.

The procedure is:

1. Read raster geotransform.
2. Extract pixel corner coordinates.
3. Convert coordinates to latitude/longitude.
4. Compute polygon area using the WGS84 ellipsoid.
5. Store the area of every pixel inside a Pixel Area Grid.

Sea Ice Area is then calculated as

```
Sea Ice Area =
Σ (Area of all pixels classified as Sea Ice)
```

This approach provides a more physically accurate estimate of Arctic sea ice extent.

---

# Annual Statistics

For every year, the following statistics are computed:

- Monthly Sea Ice Area
- Yearly Mean
- Minimum
- Maximum
- Standard Deviation

---

# Ocean Mean Albedo

Annual Ocean Mean Albedo values are merged with the Sea Ice dataset for comparative analysis.

---

# Statistical Analysis

## Descriptive Statistics

- Mean
- Median
- Standard Deviation
- Variance
- Minimum
- Maximum
- Quartiles
- Interquartile Range (IQR)

---

## Pearson Correlation

Used to quantify the relationship between

- Sea Ice Area
- Ocean Mean Albedo

Outputs

- Correlation Coefficient (r)
- p-value

---

## Mann–Kendall Trend Test

Used to determine whether a statistically significant monotonic trend exists.

Outputs

- Trend
- Z Statistic
- Kendall Tau
- S Statistic
- Variance(S)
- p-value

---

## Sen's Slope Estimator

Used to estimate the magnitude of the long-term trend.

---

# Visualizations

The project generates publication-quality figures including:

- Annual Sea Ice Area
- Average Seasonal Cycle
- Heatmaps
- Yearly Mean Arctic Sea Ice Maps
- Sea Ice Area vs Ocean Mean Albedo
- Percentage Deviation Analysis
- Trend Analysis (2000–2025)
- Trend Analysis (2000–2015)
- Trend Analysis (2016–2025)

---

# Project Structure

```
Arctic_SeaIce_Albedo_Trend_Analysis_2000_2025/

│
├── Data/
│   ├── March/
│   ├── April/
│   ├── May/
│   ├── June/
│   ├── July/
│   ├── August/
│   └── September/
│
├── Master_Dataset/
│
├── Results/
│
├── Notebook/
│
├── latitude_mask.npy
├── pixel_area_grid.npy
│
├── README.md
```

---

# Python Libraries Used

- Python
- NumPy
- Pandas
- Rasterio
- PyProj
- Cartopy
- Matplotlib
- SciPy
- pymannkendall
- OpenPyXL

---

# Output Files

The project generates:

- Master Dataset
- Annual Statistics
- Descriptive Statistics
- Pearson Correlation Results
- Mann–Kendall Test Results
- Trend Summary
- Publication Figures
- Heatmaps
- Yearly Mean Raster Maps

---

# Key Features

✔ Geodesic pixel area calculation

✔ No fixed 625 km² assumption

✔ Physically accurate sea ice area estimation

✔ Arctic region masking (60°N–90°N)

✔ Long-term trend analysis

✔ Publication-quality visualizations

✔ Fully reproducible Python workflow

---

# Author

**Durgesh Hyalij**

B.E. Computer Engineering

NRSC–ISRO Internship Project

Remote Sensing • GIS • Python • Arctic Sea Ice Analysis

---

# Acknowledgements

- National Snow and Ice Data Center (NSIDC)
- Indian Space Research Organisation (ISRO)
- National Remote Sensing Centre (NRSC)

---