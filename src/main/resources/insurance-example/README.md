# Insurance Company Example

This example is illustrates the Context Mapper DSL capabilities on the basis of a fictive insurance company scenario. 
Note that the goal of the example is to give a representative overview over the DSL's context mapping features. The contexts and their relationships may differ considerably in a real-world insurance company.

## Context Map
The following figure illustrates the Context Map in the same representation as it done by [Vernon][1] and [Brandolini][2].
You can find the corresponding context map in CML (Context Mapper Language) [here](./Insurance-Example_Context-Map.cml). Use the ContextMapper Eclipse plugin for better readability due to syntax highlighting ([Eclipse Update Site](https://dl.bintray.com/contextmapper/context-mapping-dsl/updates/)).

 * Context Mapper File: [Insurance-Example_Context-Map.cml](./Insurance-Example_Context-Map.cml) 
 * Alternative Relationship Syntax: [Insurance-Example_Context-Map_Alternative-Relationship-Syntax.cml](./Insurance-Example_Context-Map_Alternative-Relationship-Syntax.cml)
 * ServiceCutter User Representations File (for ServiceCutter integration): [Insurance-Example_Context-Map_user-representations.scl](./Insurance-Example_Context-Map_user-representations.scl) (just an example, can be regenerated by Eclipse plugin and enhanced with more details)

![Insurance Company Example Context Map](./images/ContextMap-Illustration.png "Insurance Company Example Context Map")

The following bounded contexts are involved in the system:
 * Customer Management
 * Customer Self-Service Management
 * Policy Management
 * Debt Collection
 * Risk Management
 * Printing Context
 
### Customer Management
The customer management context is responsible for managing all the data of the insurance companies customers. Thus, it is typically a central bounded context which has relationships to many other contexts.

### Customer Self-Service Management
This context represents a web application which allows the customer to login and change basic data records like the address.

### Policy Management
This bounded context manages the contracts and policies of the customers. It works in a _partnership_ together with the risk management context, since it needs the customer risk data for calculating the customer rates. Further, it has a _shared kernel_ with the debt collection context. 

### Debt Collection
The debt collection context is responsible for the financial income of the insurance company (the debts) which depend on the corresponding contracts and policies.

### Risk Management
The risk management context works in a close _relationship_ with the policy management context and calculates risks which influence contracts and policies.

### Printing Context
This context represents an external system which is accessed by an API by many internal contexts. It handles documents which have to be printed, as for example debts, policies, etc.

## Team Map
Besides classic context maps with bounded contexts, CML supports modeling teams and their relationships as it is possible with bounded contexts. This is done by simply change the type of a bounded context from SYSTEM, FEATURE or APPLICATION to TEAM. Note that the type of the context map is ORGANIZATIONAL in this case.

[Insurance-Example_Team-Map.cml](./Insurance-Example_Team-Map.cml) is an example of such a team map, again in the context of the insurance example. Besides the teams on the context map, it is possible to define which bounded contexts a team realizes.

The following figure is an illustration of the team map, additionally showing the `realization` references:

![Insurance Company Example Team Map](./images/TeamMap-Illustration.png "Insurance Company Example Team Map")

[1]: https://www.amazon.de/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577
[2]: https://www.infoq.com/articles/ddd-contextmapping