
# AstraDB Vector Collection Schema

**Collection Name**: `airline_review_rag`

## Document Structure

Each document in the `airline_review_rag` collection contains:

### `$vectorize` (string)
- The full review chunk passed to the embedding model
- Contains structured text like:

```
Title: "Usually never on time"
Review: Bangalore to Kathmandu. One of the worst airlines if you consider on time performance...
Route: Bangalore to Kathmandu
Seat Type: Economy Class
Traveller Type: Business
```

###  `$vector` (array)
- The resulting 1536-dimensional vector embedding of the `$vectorize` field (auto-managed)

### `_id` (string)
- Unique identifier for the document (auto-generated)

###  Optional metadata (if added during ingestion):
- `airline`: string (e.g., "Nepal Airlines")
- `route`: string (e.g., "Bangalore to Kathmandu")
- `seat_type`: string (e.g., "Economy Class")
- `traveller_type`: string (e.g., "Business")

