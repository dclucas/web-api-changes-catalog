# web-api-changes-catalog
A catalog of possible changes to a web API and their potential impact over clients.

## Safe changes

Rationale for all: add-only pattern should always be safe.

|           change          |   direction  |
|---------------------------|--------------|
| add optional field        | input/output |
| add operation             | input/output |
| add optional link         | input/output |
| add resource              | input/output |
| add optional parameter    | input/output |
| add media type			| input/output |


## Breaking changes

The `monitorable` column assumes a RESTful (or RESTful-like) API. The use of GraphQL, for example, would provide different monitoring opportunities. 

Please bear in mind that monitoring alone is not a guarantee: clients may simply have not be using the breaking case during your sampling.

|           change          |   direction 	| monitorable? | rationale 											|
|---------------------------|---------------|-----|-------------------------------------------------------------|
| drop default value        | output 		|  N  | Null values may not be expected		 						|
| drop field                | output		|  N  | Field may be under use		    							|
| increase field length     | output		|  Y  | Longer length may exceed client constraint					|
| decrease field length     | input 		|  Y  | Shorter length may break input								|
| drop constraint           | output		|  N  | Clients may rely on the constraint     						|
| add enum values           | output		|  N  | Clients may have hard-coded logic based on those values 	|
| remove enum values        | input 		|  Y  | Clients may send invalid enum values 						|
| drop resource             | output		|  Y  | Clients may rely on that resource 							|
| add default value         | input/output	|  N  | Clients may expect null values     							|
| change default behavior   | input/output	| Y/N | Changes to default sorting, paging, etc 					|
| change status codes       | input/output	|  Y  | Clients may use response codes to handle alternate flows 	|
| change error contracts    | input/output	|  Y  | Clients may have error handling logic that relies on it 	|
| remove media type         | input/output	|  Y  | Clients may be using media type 							|
| change field format       | input/output	| Y/N | Client logic based on format may break, input may break 	|
| change field type			| input/output 	|  N  | Structural changes will break client expectations 			|
| authorization changes     | input/output  |  Y  | Restrictint access rights may break Clients 				|
| move fields               | input/output 	|  N  | Structural changes will break client expectations 			|
| add constraint            | input 		|  Y  | New constraint will break client input 						|
