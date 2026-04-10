# Electric Vehicle Type Prediction

## Məqsəd
Avtomobil xüsusiyyətlərinə əsasən BEV (tam elektrikli) və ya PHEV (hibrid) olduğunu təsnif etmək.

## Nəticə
**XGBoost Accuracy: 80.62%**

## Feature-lar
- Model Year (47% - ən vacib)
- lat / lon (coğrafi lokasiya)
- Legislative District
- 2020 Census Tract

## Problemlər
- PHEV recall cəmi 9% (dataset balanssızdır: 80% BEV, 20% PHEV)
- Electric Range proqnozu mümkün olmadı (batareya ölçüsü yoxdur)

## Texnologiyalar
Python | Pandas | Scikit-learn | XGBoost | Matplotlib | Seaborn

## Müəllif
Orkhan Ismayilov

## Lisenziya
MIT
__pycache__/
*.pyc
.ipynb_checkpoints/
*.pkl
*.joblib
.DS_Store
venv/
.venv/
