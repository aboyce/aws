## Lambda

Lambda scales out but not up automatically, you have to increase the memory.

Lambda functions can initiate other Lambdas.

### Supported languages

- Java
- Go
- PowerShell
- Node.js
- C#
- Python
- Ruby

### Version Control

Can have multiple versions of functions, the latest will be `$latest`. Qualified version will have `$latest` unqualified will not have it.

Version are immutable.

Can split traffic using aliases to different versions, but cannot split traffic with `$latest` you have to use an alias.

### Pricing

Charged on the number of requests. First million are free then $0.20 per million. Also charged on the duration, rounded to the nearest 100ms and depends on the amount of memory you allocate.
