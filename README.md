# airbnb-analytics-munich

Data-driven revenue analysis and market segmentation of Munich Airbnb listings using multivariate linear regression and K-Means clustering. Developed as a group project at Seoul National University Business School.

## Observations & Disclaimers
The objective was to identify correlations, not causal relationships. Multicollinearity was intentionally not addressed as the priority was pattern recognition and predictive potential. The reported adjusted R² of 0.48 is an in-sample metric and does not exclude overfitting. Further due diligence is required to assess factors the model cannot capture (building condition, interior design, listing photo quality, etc.).

## Feature Engineering
Missing values were identified and imputed. Distance to key Munich landmarks (Marienplatz, Central Station, Oktoberfest venue) was computed using the Haversine formula and added as location features. The number of amenities per listing was counted and added as an additional predictor.

## Machine Learning Pipeline
Falsely set prices and inactive listings were identified and removed. The dataset was used to build and compare two OLS regression models predicting estimated annual revenue.

First, an initial model was built using numerical variables selected based on p-values, achieving an adjusted R² of 0.42. An extended model incorporating location, amenities and categorical variables was then compared to the initial model via 5-fold cross-validation. After backward elimination of insignificant predictors (p > 0.05), the final model achieved an adjusted R² of 0.48.

A "Potential" metric was defined as the gap between predicted and actual estimated revenue. Listings were segmented into three market clusters via K-Means (K=3): overperforming listings, average market segment, and undervalued listings with high investment potential.

## Files
- `airbnb-data-munich.csv`: dataset used in the pipeline
- `airbnb-munich-main.ipynb`: full Python pipeline

## Source
Cox, M. Inside Airbnb. http://insideairbnb.com/get-the-data/, 2024.
