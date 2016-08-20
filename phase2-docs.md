# Answers to Questions

Question 2.a) QN Analysis Kombat's commands to extract the osm file are:

```bash
cd C:\Program Files\osm

osm2pgsql -c -d lesotho -K -H localhost -U postgres --slim -S default.style 1808-lesotho-latest.osm.pbf (fifiQn)

cd C:\osm

osm2pgsql -c -d lesotho -K -H localhost -U postgres -S default.style 1808-lesotho-latest.osm.pbf (MontshyQn and Stanley Makhanya )
```

b) The download link we used is: **download.geofabrik.de**

c) The date of the download is : **18th August 2016**

Question 4.a) there are **[5374] mapped buildings for Urban Council** (our study area)

| Building     | Count |
|--------------|-------|
| House        | 3     |
| Church       | 4     |
| Hangar       | 1     |
| hospital     | 4     |
| industrial   | 4     |
| commercial   | 9     |
| School       | 3     |
| shed         | 87    |
| farm houses  | 4     |
| garage       | 2     |
| residential  | 5     |
| Yes          | 4493  |
| construction | 71    |
| retail       | 1     |
| hotel        | 11    |
| Hut          | 671   |
| garages      | 1     |
| **Total**        | **5374**  |

b) The Length of all Urban Council mapped roads is: **188.8466 KM**

| roads\_km        | Highway      |
|------------------|--------------|
| 22.5469253530541 | Primary      |
| 35.8166614257247 | Unclassified |
| 2.96177709353495 | Secondary    |
| 24.4303221357158 | Track        |
| 2.72863988795633 | Footway      |
| 1.62978384827992 | Service      |
| 95.351766361882  | Path         |
| 3.38068013720313 | Tertiary     |
| 82.0085191523176 | Residential  |
| **188.8466**         | **TOTAL**        |

c) The area in hectares and the count of each type of landuse is:

| Area\_ha          | Landuse     | Count |
|-------------------|-------------|-------|
| 0.188017400001474 | Cemetery    | 1     |
| 51.3395037999519  | commercial  | 8     |
| 10351.5220627495  | Farmland    | 89    |
| 7.38443475000811  | Landfill    | 1     |
| 352.585857249941  | Military    | 1     |
| 17.0787677999725  | Retail      | 2     |
| 5814.04504980008  | residential | 25    |
| 34.6249139499669  | Quarry      | 3     |
| 6.68926289997522  | Industrial  | 1     |
