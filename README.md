# Hercules-Kadmos project data flow.
This doc. describes ETL processes for Hercules project.

***

### 1. Flights data pipeline
###### Flights (PostgresDB table) ######

![PlantUML model](http://www.plantuml.com/plantuml/png/TPB1RjSm3CRlUGfh5vZ4VmymmRIXCO7O0Gcq2qALbxYR8KsAxOAwfoVfkjALqaEYVDyNM_6lvseeDdJHHMeDB8FmtRr1O25ld9Dx0U-py4DEXX4Y9z9JE1pENi7hms5QpahaXiJOhmBLhtPnZIqINCLQLw7ddch8EPTllvSUSFHalVoKrUw4zF8j6Dv6EZu2L637S0fVsodLSFZsx9poV5P_Js6859f0VNsJq3yEYl0lZBE-v1fawRFOhC-fZQg6DkXyA9ONRAtnET2Jvct0kEc-o4lhvTaN3oK4bsW8LoMKPPoUYmxBjG_92tKq3VtTbsle9VkJoVb8uvlLC62lu3N-eAbOwzfofLq6ZF9p88EM8-d9yT-hDqo_OU7mMEZpcB1NWek4SInqzH67EdsE0vnkUEX_UUW-ZwBlyz1T7hhceJiyT9_7Ijwq7lg0HarTZBiIBH_NtxpYcFOwoRghEwSKXYx-0G00)




@startuml
left to right direction
' Horizontal lines: -->, <--, <-->
' Vertical lines: ->, <-, <->
title Flights pipeline


object "Flights (PostgresDB table)" as i
i : [flight_id]
i : [flight_no]
i : [scheduled_departure]
i : [scheduled_arrival]
i : [departure_airport]
i : [arrival_airport]
i : [status]
i : [aircraft_code]
i : [actual_departure]
i : [actual_arrival]

object "Azure Data Factory" as a
a : Incremental ETL proc.
a : Key=[flight_id] 

object "Azure DataLake" as f
f : flights (Parquet files.)

object "View Flights (Azure Synapse Analytics)" as s
s : [flight_id] 
s : [flight_no]
s : [scheduled_departure]
s : [scheduled_arrival]
s : [departure_airport]
s : [arrival_airport]
s : [status]
s : [aircraft_code]
s : [actual_departure]
s : [actual_arrival]
s : [update_datetime]



i --> a
a --> f
f --> s
@enduml
