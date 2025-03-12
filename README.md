# OFM

## Assimilating River Depth and Uncertainty Using Operator Flow Matching and Stochastic Process Learning
Objective & Research Question: The primary objective is to develop a stochastic process learning framework based on Operator Flow Matching (OFM) to assimilate river depth measurements and associated uncertainties. The research question is: How to use stochastic operator flow matching approach to effectively predict river depth by assimilating satellite-derived surface water observations and their uncertainties?
Traditional methods (like Kalman Filter variations) typically rely on Gaussian assumptions [1] and linear approximations, limiting their performance with nonlinear, high-dimensional, or non-Gaussian geospatial data. Required computation is also another limitation[2]. OFM addresses these limitations through a more flexible, data-driven approach.

Data Sources:
- SWOT (Surface Water and Ocean Topography) [3] data: Includes water surface elevations and slopes along with their associated uncertainties; resolution ~50-100m, temporal coverage from 2022-present, available publicly from NASA's DAAC archives.

- MERIT DEM [4] : A publicly available high-resolution (~90m globally) dataset providing elevation information, spatial coverage global, available from MERIT Hydro repository. 

- USGS gauge station river depth data [5]: Ground observations providing accurate depth measurements with temporal coverage varying by station, publicly accessible from USGS National Water Information System (NWIS).

Methodology: The project will utilize Operator Flow Matching (OFM), a novel method for stochastic process learning, as described by [6]. SWOT-derived water surface elevation and slope data, along with associated uncertainty, and MERIT DEM elevation data will serve as model inputs, while USGS gauge station river depth data will serve as the target variable. The data will be spatially and temporally aligned, preprocessed to handle missing values and normalized appropriately. A Python code will be developed, utilizing PyTorch and/or Nvidia modulus for neural network modeling. The Operator Flow Matching approach will employ Fourier Neural Operators (FNO) [7] for efficient computation and scalability. Training and test datasets will be strictly separated by geographic location to avoid data contamination.
Validation & Assessment: Model performance will be assessed using independent USGS ground observations. Metrics such as Root Mean Squared Error (RMSE), and Mean Absolute Error (MAE) will be employed. Uncertainties will be directly modeled and propagated using the stochastic nature of the operator flow matching approach, with robustness checked against multiple test scenarios at distinct geographical locations.

Expected Outcomes:
- Predictive models assimilating SWOT and MERIT DEM data, providing river depth predictions with uncertainty quantification.
- Geospatial visualizations illustrating spatial patterns of predicted depth and uncertainty.
- A GitHub repository containing data preprocessing scripts, trained model implementations, and analyses.
- Insights anticipated from the model will improve understanding of river dynamics under uncertainty, enhancing applicability of earth observation data.

## References:


- [1]	B. Wang, Z. Sun, X. Jiang, J. Zeng, and R. Liu, “Kalman Filter and Its Application in Data Assimilation,” Atmosphere, vol. 14, no. 8, Art. no. 8, Aug. 2023, doi: 10.3390/atmos14081319.
- [2]	K. Kurosawa and J. Poterjoy, “Data Assimilation Challenges Posed by Nonlinear Operators: A Comparative Study of Ensemble and Variational Filters and Smoothers,” Mon. Weather Rev., Jan. 2021, doi: 10.1175/MWR-D-20-0368.1.
- [3]	“SWOT Level 2 River Single-Pass Vector Reach Data Product, Version 2.0.” NASA/JPL/PODAAC, Jul. 20, 2022. Accessed: Jan. 20, 2025. [Online]. Available: https://catalog.data.gov/dataset/swot-level-2-river-single-pass-vector-reach-data-product-version-2-0-58b1b
- [4]	D. Yamazaki et al., “A high‐accuracy map of global terrain elevations,” Geophys. Res. Lett., vol. 44, no. 11, pp. 5844–5853, Jun. 2017, doi: 10.1002/2017GL072874.
- [5]	“USGS Current Water Data for the Nation.” Accessed: Feb. 25, 2025. [Online]. Available: https://waterdata.usgs.gov/nwis/rt
- [6]	Y. Shi, Z. E. Ross, D. Asimaki, and K. Azizzadenesheli, “Stochastic Process Learning via Operator Flow Matching,” Jan. 09, 2025, arXiv: arXiv:2501.04126. doi: 10.48550/arXiv.2501.04126.
- [7]	N. Kovachki, Z. Li, B. Liu, K. Azizzadenesheli, K. Bhattacharya, and A. Stuart, “Neural Operator: Learning Maps Between Function Spaces With Applications to PDEs”.
