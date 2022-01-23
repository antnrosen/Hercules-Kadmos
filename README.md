# Hercules-Kadmos project data flow.
This doc. describes ETL processes for Hercules project.

***

### Flights Pipeline
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


### Airports_data pipeline
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

![PlantUML model](www.plantuml.com/plantuml/png/RPBFJiCm3CRlUGfh5pQ9xW4cD6reJ1nsG0BjWgRAIzrXI9EIk4BTqzDaVwh2BadpVPyJ-wSkWg2NfZBAK2aW3ZmVFWGAzgI5dLLtyEmy7vqLD63OKfX1bitluI7BqZBl8blomheF93_QdIiiXW3PryvBo0iKX9fhYb6btFwJjC1ew8zVN923fx1w1C6zeSa8C00hXXcydxEvTWNjXfB5wY9fblRowPmlsA9GE2l25NKpqQxlO7biFC4gFhz6BSwtwKrKs1Mi6sEWP4EG-djwsq3jdPxUAj_W5wNIKfKmkquEunhzTqEIxfbE-j8jqmyihx7JJQ-jnJeGB2sQLbY74uAWmdy4uI-2dEmjrJUTUc7JP-AfzmQmmX1MEZPrqPbvN3ed8kJuHoHISOzZnpse1TcYgSml)

***

