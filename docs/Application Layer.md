#Application Layer

##Primary Responsibility
- Implements the search logic and data update mechanisms.

##Key Modules
* Trie Structure
<br> Implemented in **`StationTrie.cs`** 
<br><br>
* TrieNode
<br> enabling fast searching of stations based on a prefix.
<br><br>
* DTO
<br> **`StationDTO.cs`** defines a data transfer object containing two lists: Stations and NextCharacters
<br><br>
* Services
<br> **`StationSearchService.cs`**:
<br> Initializes the trie using data from the repository, cleans station names using NameCleaner.CleanName, performs the search by prefix, and returns the result as a DTO.
<br><br> **`StationUpdateDatabaseService.cs`**:
<br> A background service (inheriting from BackgroundService) that periodically (every 12 hours) fetches new data, updates the repository, and refreshes the trie structure, handling exceptions and logging events.