# Hercules project data flow.
This document describes ETL processes for Hercules project.

***

### Flights pipeline
1. Flights (PostgresDB table)
```
DataBase Name:    Flights-PostgresDB
Table Name:       Fights
```
2. Azure Data Factory
```
Tool:           Azure Data Factory
Pipeline Name:  flights_to_dl
Details:        Incremental ETL process. Key=[flight_id]
```
3. Azure DataLake
```
Folder Name:  data/kadmos_dl/flights
File Formate: parquet
Mode:         append
```
4. View Flights (Azure Synapse Analytics)
```
Tool:       Azure Synapse Serverless Pool
Table Name: [dbo].[v_flights]
```

![PlantUML model](http://www.plantuml.com/plantuml/png/TPB1RjSm3CRlUGfh5vZ4VmymmRIXCO7O0Gcq2qALbxYR8KsAxOAwfoVfkjALqaEYVDyNM_6lvseeDdJHHMeDB8FmtRr1O25ld9Dx0U-py4DEXX4Y9z9JE1pENi7hms5QpahaXiJOhmBLhtPnZIqINCLQLw7ddch8EPTllvSUSFHalVoKrUw4zF8j6Dv6EZu2L637S0fVsodLSFZsx9poV5P_Js6859f0VNsJq3yEYl0lZBE-v1fawRFOhC-fZQg6DkXyA9ONRAtnET2Jvct0kEc-o4lhvTaN3oK4bsW8LoMKPPoUYmxBjG_92tKq3VtTbsle9VkJoVb8uvlLC62lu3N-eAbOwzfofLq6ZF9p88EM8-d9yT-hDqo_OU7mMEZpcB1NWek4SInqzH67EdsE0vnkUEX_UUW-ZwBlyz1T7hhceJiyT9_7Ijwq7lg0HarTZBiIBH_NtxpYcFOwoRghEwSKXYx-0G00)

***


### Airports pipeline
1. airports_data (PostgresDB table)
```
DataBase Name:    Airports-PostgresDB
Table Name:       airports_data
```
2. Azure Data Factory
```
Tool:           Azure Data Factory
Pipeline Name:  airports_to_dl
Details:        Full file data ETL process.
```
3. Azure DataLake
```
Folder Name:  data/kadmos_dl/airports
File Formate: parquet
Mode:         overwrite
```
4. View Flights (Azure Synapse Analytics)
```
Tool:       Azure Synapse Serverless Pool
Table Name: [dbo].[v_airports]
```

![PlantUML model](http://www.plantuml.com/plantuml/png/RPBDRk8m4CVlVeeHbmLfmmEW5O8LY_R0eL8hBXMA1cT2ftNir9we2azVsn1552vs_F_mnqzP1K4lNMEKeLf077W-lGbKx4aBEwj-mN_d-Uoie073bi82YcBv6_uKHHwMCR8dBwp7GFQJ7LrXCGHhzgtp4g3bbb9AANTy9oqmmQjLLYW8qoSNvEGfRFw2uD7GR08OW1N30bwlsLAxYWwtaiLca3HBFtmwvoksA1IkYd13yJbq66-mFdUUO9EEtw8Mv_jy9YgCXMrd3DHi2FBz_htieFLEpn_LT_X1kLghEbQ7by6qHV_PaUHzvhEnkcVw6jbCBpizznRR49bPDBsm3XS4GOLx1E4dWfBi8zLtKHtOZ9cyojuTh70BAo-xjefccORe98ISVePCAixvsMaEQaMswXhp3G00)

***


### Aircrafts pipeline
1. aircrafts.csv (BLOB storage)
```
Tool:         Azure BLOB storage
Folder Name:  data/files
File Formate: csv
File Name:    aircrafts.csv
```
2. Databricks & Azure Data Factory
```
Tool:           Azure Data Factory & Databricks
Pipeline Name:  aircrefts_to_dl
Details:        Full file data ETL process.
```
3. Azure DataLake
```
Folder Name:  data/kadmos_dl/aircrafts
File Formate: parquet
Mode:         overwrite
```
4. View Aircrafts (Azure Synapse Analytics)
```
Tool:       Azure Synapse Serverless Pool
Table Name: [dbo].[v_aircrafts]
```

![PlantUML model](http://www.plantuml.com/plantuml/png/RL51R_8m3BtdLrWSlW-abH-09WHeGpiWxR29ouIGILtc4PBCSJULNx-c7VIoGstNVkyfpruaHT7wx8oZIa4321_V5KeMiih1c__m58GlmIiwSEmfpQ0evdTmNnHTcBUGBOco7G3zF7zpewoEOCbY1IjD43bIXXaJ3Xza5KPudKrj-eBnQlEyWgH1y4YJ4M02DWmpUBlYzZQKjEjxvxPqlxMWFz9kq7r0nOEmFINu1yjBBGIv1Mkq6gJffD5WIrtNpa75Zg3CWCVN3KG9TZfe3VGDdgYZLgPggNWpDeuedpLf9pIT3DmjqtTUG0oIORtKI-Cn9eAbHzSeszHRJIRzOJNThEx9vz_1RLVNiKIbVGxAvxm3paVAxdBkdffpCWloPNlk7m00)
