# Testing Overview

The tests are organized by application layer and are contained within their respective test projects.

## API and Helper Tests

- **`StationControllerTests.cs`** (TrainTicketMachine.API.Tests)**
  - **Endpoint Tested:** GET /api/stations/search
  - **Test Cases:**
    - When no prefix is provided, it returns all stations (e.g., "DARTFORD", "LIVERPOOL").
    - When a non-matching prefix is provided, it returns an empty result.

- **Helper Module Tests**
  - **`InputValidatorTests.cs`**
    - Validates that sanitization methods remove script tags, on-event attributes, and the "javascript:" protocol.
    - Checks for protection against SQL injection risks.
  - **LoggerConfigurationTests.cs**
    - Ensures that `GetAndCreateLogFolder` returns the correct log path.
    - Confirms that the method creates the necessary directory on different operating systems.

## Application Layer Tests

- **`StationSearchServiceTests.cs` (TrainTicketMachine.Application.Tests)**
  - **Scenarios Tested:**
    - Returns matching stations and the corresponding “next characters” for a given prefix (e.g., for "DART", returns "DARTFORD" with "F" and "DARTON" with "O").
    - Ensures that station names are cleaned correctly by removing unwanted characters.
    - Handles scenarios when the repository is empty or the prefix does not match any station.
    - Tests `TryUpdateTrieAsync` for:
      - Uninitialized trie.
      - New data that is identical to current data.
      - New data that differs from the current data.

- **`StationUpdateDatabaseServiceTests.cs`**
  - Verifies that the background service updates both the repository and trie when new data is successfully fetched.
  - Ensures that no update is performed if an exception occurs during data retrieval.

## Domain Layer Tests

- **`StationModelTests.cs`** (TrainTicketMachine.Domain.Tests)**
  - Tests the station model's constructor and the `IsValid()` method.
  - Confirms proper initialization and validation of the station properties.

## Infrastructure Layer Tests

- **JsonUrlDataSourceTests.cs (TrainTicketMachine.Infrastructure.Tests)**
  - Validates that `GetStationsAsync` throws a JSON exception when provided with invalid JSON data. [97]

- **`StationRepositoryTests.cs`**
  - Ensures that the repository returns an empty collection when the data source provides an empty list.