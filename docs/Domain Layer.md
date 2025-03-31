#Domain Layer 

##Primary Responsibility
- Define domain models and contracts (interfaces) used by other layers.

##Key Components
- **`StationModel.cs`** represents a station with properties Code and Name, and includes an `IsValid()`.
<br>
##Interfaces
- **`IStationRepository.cs`**
<br>
Defines methods for retrieving all stations and updating the database.

- **`IStationDataSource.cs`**
<br>
Defines an asynchronous method to fetch station data