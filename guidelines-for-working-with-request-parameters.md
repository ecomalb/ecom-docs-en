# Guidelines for Working with Request Parameters

mportant: If a parameter is optional (non-mandatory), it is highly recommended to omit it from the request entirely.

If an optional parameter is passed in the request, the system automatically applies validation to it, including:

* Checking for the absence of a value (`null`);
* Compliance with the specification (format, data type, range of values, etc.).

#### Consequences

If a client passes an optional parameter with a `null` value or in an incorrect format, the system will return a validation error, which may lead to the rejection of the request processing.

#### Recommendations for Clients

* Carefully check all parameters being passed, paying attention to:
  * The parameter's mandatory status (indicated in the documentation as required or optional);
  * The expected data type and format (e.g., `string`, ISO 8601 timestamp).
* For optional parameters:
  * Omit the parameter from the request if it is not being used;
  * Avoid passing explicit `null` or empty values.
