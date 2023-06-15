Most parameters are optional and some combinations might not return a payload. If you feel that there should be data for a particular combination of filters, please reach out to [ctdata@mskcc.org](mailto:ctdata@mskcc.org).


| Parameter      | Type    | Is Required | Description                        |
| -----------    | ------- | ----------- | ---------------------------------- |
| category       | string  | false       | Applies to observation resource and can take laboratory, vital-signs or imaging values. If not used the observation resource requires "code" parameter which would return the filtered records from laboratory and vital-signs. |
| _count         | integer | false       | Controls the number of records returned in the bundle. The default is `50` records. Use this parameter wisely to avoid timeout errors. |
| code           | string  | false       | Returns the records for the given LOINC Code. Follows the format `&code=http://loinc.org|777-3,http://loinc.org|751-8` <br> Applies to Observation resource.|
| component-code | string  | false       | Returns the records for the given LOINC Code. Follows the format `&component-code=http://loinc.org|777-3,http://loinc.org|751-8` <br> Applies to Observation resource.|
| date           | date    | false       | Must follow the format `&date=OpMM/DD/YYYY` or date range as `&date=OpMM/DD/YYYY&date=OpMM/DD/YYYY` where OP is the Operator for that date. Acceptable values include: <ul><li>eq (==)</li><li>ne (! =)</li><li>lt (< )</li><li>gt (>)</li><li>ge (>=)</li><li>le ( <=)</li></ul>|
| _format        | string  | false       | When set to `&_format=json` it returns Content-Type of the response in application/json format. By default it is set to text/plain |
| _id            | string  | false       | Returns the record for a given ID |
| issued         | date    | false       | Returns the records for the issued date. Must follow the format `&issued=OpMM/DD/YYYY` where OP is the Operator for that date. Acceptable values include: <ul><li>eq (==)</li><li>ne (! =)</li><li>lt (< )</li><li>gt (>)</li><li>ge (>=)</li><li>le ( <=)</li></ul> Must be used against Observation resource.|
| page           | integer | false       | Used to retrieve data on a particular page. Refer to [pagination](pagination.md) for more details. |
| _sort			 | string  | false       | Returns the records in sorted order. The prefix '-' indicates decreasing order; in its absence, the parameter is applied in increasing order.|
| researchstudy  | string  | true*       | MSK unique study number           |
| studyid        | string  | **          | Sponsor study ID                  |

*True for all resource requests except /Patient, which require one of the following to return data: researchstudy or {id}. Patient requests submitted using {id} will return data only if that subject is part of the studies `x-partnerid` has access to.

** Not available yet