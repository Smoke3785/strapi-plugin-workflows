# strapi-plugin-workflows

## Key Concepts

### Triggers
- Triggers serve as entry points for flows. Each flow can have an indefinite number of triggers.
- Some pre-baked trigger types include:
  - Webhook/endpoint
  - Content Type CRUD
  - CRON job
  - Lifecycles (v4/v5 is different...)
  - Internal triggers (via service API)
- Users should also be able to define arbitrary trigger types. All user-added customization should occur during the bootstrap lifecycle hook.
  - We need to register hooks in the registry before bootstrap occurs so users can inject custom functionality.
 
### Logic
- ~~Basic logical operators~~
  - ~~IF ingests data, outputs data on two edges, TRUE or FALSE based on the value of the resolved condition. Third edge is ERROR.~~
  - ~~AND, OR, XOR, NOT eat farts~~
- Condition block, that takes an input and uses it as the input for a user-defined filter.
- Filters are expressed in the same was as CRUD/REST filters in [strapi](https://docs.strapi.io/dev-docs/api/document-service/filters). Inputs are validated against this filter, which can inpterpolate values from previous operations by using templating e.g. `{{operationkey.operationvalue}}`.
- Conditions have three edges, ERROR, TRUE, FALSE.
-

- Array operators? At least forEach

- Each node has input data of a specific type. If the data entered does not match the type, throw an error.

- Each logic node takes in **ONE** input, but can output **ONE** of **MANY** output types **OR** an error.
- All nodes are promises that call their outputs as side effects of resolution.
- Logical operators have three edges, TRUE, FALSE, or ERROR.

### Actions
- Actions have two edges, one for ERROR, and one titled OUTPUT (owen likes THEN) which executes upon resolution.

- CRUD operations
- Send webhook/API request
- Trigger another action
- Email actions (integrate with Unlayer?)
- Log to console
- Trigger custom code

- Injectable

### Nodes
- Each node has a name, and the UNIQUE name is used as a key for its data in the accumulated context object for each flow.
- Each node has access to its input, in addition to the outputs of all previous operations. Input is fundemantally the same as the rest of the outputs, just has a [generic name](https://www.youtube.com/watch?v=Rlof69dpZSo&t=396s).
- 

## Considerations
- Represent each node as a class? OOP maxxing?
