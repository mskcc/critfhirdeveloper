Errors and warnings are communicated using the [OperationOutcome](https://hl7.org/fhir/2021Mar/operationoutcome.html) resource. See below for examples of the types of errors supported by Blaze.

## Response

??? Error "Error Payload Example"
    ```json
    {
        "resourceType": "OperationOutcome",
        "issue": [
        {
            "severity": "error",
            "code": "value",
            "details": {
            "text": "Unable to find sponsor with partner id"
            }
        }
        ]
    }
    
    ```

   
### Error Codes

| Error Code  | Issue Type  |  Description                            | Example                                                                               |
| ----------- | -------     |  ------------                           | ----------------------------------                                                    |
| 400         | Error       |  Missing required query parameter       | The required parameter, Research Study, is not provided.                              |
| 401         | Error       |  Incorrect Partnerid name               | The header should contain `x-partnerid` with provided Partner Id parameter.           |
| 401         | Error       |  Api Key was not provided               | Missing Partner Id parameter value in the request header.                             |
| 403         | Security    |  Access to sponsor denied               | The partner ID does not have access to the Sponsor id provided.                       |
| 403         | Security    |  Access to protocol denied              | The partner ID doesn't have access to the Research Study/Protocol provided.           |
| 403         | Security    |  Access to sponsor and protocol denied  | The partner Id does not have access to the Sponsor and Protocol/Research Study given. |
| 404         | Error       |  Unable to find sponsor with partner id | The sponsor is not associated with the given Partner Id.                              |
| 404         | Exception   |  Internal Error                         | Internal Error occured while executing the request.                                   |
| 404         | Information |  No records found                       | No records were found for the given request.                                          |
