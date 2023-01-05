# Why invariants?

- The main reason in my opinion one should use invariant tests rather than unit/integration tests with similar assertions/requirements is in order to traverse different scopes (this can be a single contract, single caller or multiple contracts, multiple callers) with arbitrary/pseudo-random call chains programmatically, so the developer does not need to recognize or know about all call chain possibilities in order to write out and test them. In the case of "SimpleInvariant" it is reasonable to assume that a developer would be able to map out manually with unit tests all possible call chains and things that could happen in the contracts scope, testing each of them individually. Nonetheless for situations involving several contracts, or more complicated contracts the ability to find all these possibilities becomes more cumbersome and sometimes just straight up impractical in terms of time commitment alone. It is better to define an invariant you want to hold for a given scope and have the foundry back-end do the work for you fuzzing it, than to think about all the possible call chains in that same scope and write out test functions for each call chain starting from the initial state made by the setUp() function.