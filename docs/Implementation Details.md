# Implementation Details

## API
- **`StationsController.cs`**
	- The endpoint GET /api/stations/search accepts the prefix query parameter.
	- Input validation is performed using InputValidator.
	- In case of invalid input, a 400 Bad Request is returned.
	- The search result is returned as a StationDto.
## Application Logic
- Trie Structure (**`StationTrie.cs`**, **`TrieNode.cs`**)
<br>
	- The Insert method adds a station to the trie.
	- The Search method returns both a list of words matching the prefix and a list of "next characters".
<br><br>
- DTO (**`StationDTO.cs`**)
	- Contains two lists: Stations and NextCharacters.
<br><br>
- Services
	- **`StationSearchService.cs`**
	- Initializes the trie using data from the repository (via the `IStationRepository` interface), cleans station names using `NameCleaner`, and performs the prefix-based search
<br><br>
- **`StationUpdateDatabaseService.cs`**
	- A background service that periodically fetches new data from an external source, updates the repository, and refreshes the trie, handling exceptions and logging events.
	
## Domain and Infrastructure Layers

- Domain
	- **`StationModel.cs`** represents a station.
	- Interfaces IStationRepository and IStationDataSource define the contracts for data access.
<br><br>
- Infrastructure
	- **`JsonUrlDataSource.cs`** fetches and maps JSON data to `StationModel` objects.
	- **`StationRepository.cs`** implements in-memory storage and update mechanisms for station data.
	
## Helper Modules
- `InputValidator`, `LoggerConfigurationHelper`, `NameCleaner`
	- These modules provide input sanitization, log configuration, and data cleaning functions.