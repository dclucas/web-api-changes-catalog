# web-api-changes-catalog
A catalog of possible changes to a web API and their potential impact over clients.

## Safe changes
|           change          |   direction  | rationale |
|---------------------------|--------------|-----------|
| add optional field        | input/output | |
| add operation             | input/output | |
| add optional link         | input/output | |
| add resource              | input/output | |
| add optional parameter    | input/output | |
| add media type			| input/output | |


## Breaking changes

The `monitorable` column assumes a RESTful (or RESTful-like) API. The use of GraphQL, for example, would provide different monitoring opportunities. Please bear in mind that monitoring alone is not a guarantee: clients may simply have not be using the breaking case.

|           change          |   direction  | monitorable? | rationale |
|---------------------------|--------------|---|----------------------|
| drop default value        | input/output | N | Clients may see unexpected null values |
| drop field                | output       | N | Clients may rely on the field          |
| increase field length     | output       | Y | Clients may expect shorter fields      |
| decrease field length     | input        | Y | Clients may expect to send longer data |
| drop constraint           | output       | N | Clients may rely on the constraint     |
| add enum values           | output       | N | Clients may have hard-coded logic based on those values 	|
| remove enum values        | input        | Y | Clients may send invalid enum values 						|
| drop resource             | output       | Y | Clients may rely on that resource 							|
| add default value         | input/output | N | Client may expect null values           |
| change default behavior   | input/output | Y | Changes to default sorting, paging, etc |
| change status codes       | input/output | Y | |
| change error contracts    | input/output | Y | |
| add constraint            | input        | Y | |
| remove media type         | input/output | Y | |

/Y*: yes, to a degree./