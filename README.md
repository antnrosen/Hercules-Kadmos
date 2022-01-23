# Hercules-Kadmos project data flow.
This doc. describes ETL processes for Hercules project.
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
