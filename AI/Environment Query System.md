- The Environment Query System collects data from the environment, enabling AIs to inquire about the data using various tests.
- Queries can be called from a *behavior tree* and used to make decisions on how to proceed based on the results of the executed tests.

```
Artificial Intelligence -> Enviroment Query
```

- Collect data from the environment
- Instruct AI character to find the best possible location

### Generator

- Produce points (refer as Items)
-  Items will be tested and weighted
- Return highest weight item to behavior tree

### Context

- Provide reference point for generators
- Can be as simple as the querier (**Enemy**)

### EQS Test Pawn

- EQSTestingPawn (Blueprint)
- Query Template (Enviroment Query)

### Test

- Determine which Item produced from the Generator is the best

### Filter

-  Remove failed items

### Score

- Assign weight to each item

---
## Details

### OnCircle

- Circle Center: [[EnvQueryContext_BlueprintBase]]

