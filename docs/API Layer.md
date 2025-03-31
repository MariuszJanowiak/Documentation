#API Layer

##Primary Responsibility
- Expose RESTful endpoints.

##Key Component

- **`StationsController.cs`**
<br> The endpoint GET /api/stations/search accepts the prefix parameter from the query string, validates it using the **InputValidator**, and calls the search logic in **StationSearchService**.