#Infrastructure Layer

##Primary Responsibility
- Data access, repository implementation, and mapping external data to domain models.

##Key Components

- Data Access
<br>
**`JsonUrlDataSource.cs`** 
Implements IStationDataSource – fetches data from an external class being interpretation of required data source (JSON in this case), deserializes it, and maps it to StationModel objects.
<br><br>
- Transfer Data to object
<br>
DTO **`StationJsonDto.cs`** for mapping JSON data (with properties stationCode and stationName).
<br><br>
- Repository
<br>
**`StationRepository.cs`** Implements IStationRepository by storing station data in memory and enabling updates with thread safety.