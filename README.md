[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/OrkhanIsmayilov992/electric-vehicle-type-prediction/blob/main/Electric_Vehicle_Population_Data.ipynb)

🚗 Elektrikli Avtomobillərin Təsnifatı və Analizi
📌 Layihə haqqında
Bu layihədə elektrikli nəqliyyat vasitələrinin (Electric Vehicles) xüsusiyyətlərinə əsaslanaraq onların BEV (Battery Electric Vehicle) və PHEV (Plug-in Hybrid Electric Vehicle) kimi təsnifatı həyata keçirilmişdir.

Layihə yalnız model qurmaqdan ibarət deyil — burada real dünya data problemləri (çatışmayan dəyərlər, uyğunsuz məlumatlar, balanssız siniflər və s.) sistemli şəkildə analiz edilmiş və həll olunmuşdur.

🎯 Məqsəd
Layihənin əsas məqsədi:

Elektrikli avtomobillərin tipini (BEV vs PHEV) proqnozlaşdırmaq
Data keyfiyyətini artırmaq üçün effektiv preprocessing strategiyaları tətbiq etmək
Data leakage və zəif feature-ları aradan qaldırmaq
Real data üzərində etibarlı model qurmaq
🧹Data Preprocessing və Cleaning
🔍 Çatışmayan dəyərlərin (NaN) analizi
Datasetdə bəzi coğrafi sütunlarda (County, City, Postal Code, Electric Utility, 2020 Census Tract) çatışmayan dəyərlərin eyni sətirlərdə yerləşdiyi müşahidə edildi.

Bu nəticə göstərir ki:

məlumatlar təsadüfi yox, blok şəklində itirilib
bu cür məlumatlar birlikdə analiz olunmalıdır
🧹 NaN dəyərlərin idarə olunması
Model üçün kritik olan sütunlarda (Legislative District, Vehicle Location, Electric Range) çatışmayan dəyərlər silindi.

Qərarın səbəbi:
NaN sayı ümumi datasetə nisbətən çox az idi
bu sətirlərin silinməsi model nəticəsinə ciddi təsir etmirdi
data keyfiyyətini artırırdı
⚡ Lazımsız sütunların çıxarılması
Aşağıdakı sütunlar datasetdən çıxarıldı:

Unikal identifikatorlar (VIN, DOL ID)
Redundant və az faydalı sütunlar (State, Postal Code)
Məqsəd:
Dataset ölçüsünü azaltmaq
Hesablama sürətini artırmaq
Modelin yalnız faydalı məlumatlara fokuslanmasını təmin etmək
📊 Exploratory Data Analysis (EDA)
🔢 Statistik analiz
Əsas numeric sütunlar üzərində analiz aparıldı:

Model Year
Electric Range
Bu analiz vasitəsilə:

dəyərlərin paylanması
outlier-lar
ümumi trendlər müəyyən edildi
📌 Kategorik dəyişənlərin analizi
Kategorik sütunlarda unikal dəyər sayı yoxlanıldı.

Məqsəd:
yüksək kardinalı dəyişənləri müəyyən etmək
encoding strategiyasını planlamaq
⚠️ Domain knowledge əsaslı qərar
“CAFV Eligibility” sütunu üzrə bəzi avtomobillər üçün:

“Eligibility unknown as battery range has not been researched”

Bu dəyərlər dəyişdirilmədi.

Səbəb:
bu status real dünyada dövlət qeydiyyatı ilə bağlıdır
model üçün süni dəyişiklik etmək düzgün deyil
🚨 Data Problemləri və Həllər
🔻 Electric Range = 0 problemi
Bəzi avtomobillər üçün elektrik məsafəsi 0 kimi göstərilmişdir.

Həll:
həmin avtomobilin modeli üzrə maksimum dəyər istifadə edildi
Məntiq:
0 real texniki göstərici deyil
model səviyyəsində ən real dəyər maksimumdur
🔻 Az müşahidəli markalar
Bəzi markalarda müşahidə sayı çox az idi.

Qərar:
bu markalar datasetdən çıxarıldı
Səbəb:
modelə noise əlavə edir
balansı pozur
ümumiləşdirməni zəiflədir
📊 Statistik Analiz
🧪 Chi-Square testləri
Aşağıdakı dəyişənlər arasında əlaqə yoxlanıldı:

Marka və avtomobil tipi
Marka və CAFV statusu
Avtomobil tipi və CAFV statusu
Nəticə:
dəyişənlər arasında statistik olaraq əhəmiyyətli əlaqə mövcuddur
bu feature-lar model üçün informativdir
🌍 Feature Engineering
📍 Coğrafi məlumatların çıxarılması
“Vehicle Location” sütunundan koordinatlar (latitude və longitude) çıxarıldı.

Əhəmiyyət:
coğrafi məlumatlar modelə əlavə olundu
region əsaslı analiz mümkün oldu
🧠 Model Qurulması
🔹 Feature Selection
Model üçün aşağıdakı əsas dəyişənlər seçildi:

Model Year
Legislative District
2020 Census Tract
Latitude / Longitude
🔹 Data Transformasiya
Kategorik dəyişənlər encode edildi
Bütün dəyişənlər scale olundu
🔹 Train/Test bölünməsi
Dataset:

80% training
20% testing
Stratified bölünmə istifadə edildi ki, sinif balansı qorunsun.

🤖 Modellər
Aşağıdakı modellər sınaqdan keçirildi:

Random Forest
XGBoost
📊 Nəticələr
Ən yaxşı model: XGBoost
Accuracy: ~80.6%
📈 Feature Importance
Ən vacib dəyişən:

Model Year (~47%)
Digər vacib faktorlar:

coğrafi məlumatlar
inzibati bölgələr
📉 Problemlər və Məhdudiyyətlər
🔻 Class Imbalance
PHEV sinfi zəif tanındı
Recall ≈ 9%
🔻 Feature çatışmazlığı
Batareya ölçüsü yoxdur
Electric Range kifayət qədər informativ deyil
🔻 SMOTE uğursuz oldu
siniflər arasında overlap mövcuddur
oversampling nəticəni yaxşılaşdırmadı
📈 Əsas Insight-lar
Yeni model illəri daha çox BEV-dir
Coğrafi faktorlar təsir göstərir
Feature keyfiyyəti modeldən daha vacibdir
⚙️ Model optimizasiyası
Hyperparameter tuning tətbiq edildi və model performansı optimallaşdırıldı.

✅ Yekun
Bu layihə göstərir ki:

Data preprocessing modeldən daha vacib mərhələdir
Data leakage düzgün idarə olunmalıdır
Real data ilə işləmək nəzəriyyədən daha çətindir
🧰 İstifadə olunan texnologiyalar
Python
Pandas, NumPy
Scikit-learn
XGBoost
Matplotlib, Seaborn
💼 Portfolio və iş müraciəti üçün dəyər
Bu layihə aşağıdakı bacarıqları nümayiş etdirir:

Data Cleaning
Feature Engineering
Statistical Analysis
Machine Learning Modeling
Real-world Problem Solving
