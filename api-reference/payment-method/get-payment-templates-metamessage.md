# Get Payment Templates Metamessage

#### Get Payment Method Templates Metamessage

This API retrieves the template details for various payment methods metamessage on the provided payment method ID.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Method**: `GET`
* **Request Path**: `/v2/payments/templates/metamessage`
* **Authorization Required**: Yes

#### Query Parameters

* **paymentId**: (int) The ID of the payment method.

#### Response Structure

**Field metadata description:**

* **index:** (number) The sequential number identifying the field's position.
* **indexCode:** (string) A unique code or identifier for the field. If this field is not empty, then when adding the payment method, use this field for submission.
* **title:** (string) The display label or name of the field. When the indexCode is empty, use this field name when providing payment method information.
* **textType:** (enum) Numeric code indicating the type or format of the text input.
  * **1: number** — Numeric characters only (0–9).
  * **2: letter** — Alphabetic characters only (A–Z, a–z).
  * **3: alphanumeric** — Letters and numbers only.
  * **4: string** — Any free‑text string.
  * **5: image** — Image data or a reference to an image.
  * **6: ISO 3166‑1** — Country code (e.g., US, CN, JP).
  * **7: ISO 3166‑2** — Subdivision code (e.g., US‑CA, CN‑BJ).
  * **8: international dialing code** — Country calling code (e.g., 1, 86).
  * **9: date (fixed format)** — Date in `yyyy‑MM‑dd` format (e.g., 2026‑04‑17).
  * **10: dropdown list** — The field is an enumerated value presented as a dropdown. The `extendInfo` field stores a JSON string that defines the options, e.g., `[{"code":"CURP","name":"Curp type"},{"code":"RFC","name":"Rfc type"}]`.
* **promptText:** (string) Placeholder or instructional text shown inside the input field.
* **minLimit:** (number) Minimum allowed value or length for the field input.
* **maxLimit:** (number) Maximum allowed value or length for the field input.
* **isOptional:** (boolean) Indicates whether the field is optional (true) or required (false).
* **isAccount:** (boolean) Specifies whether the field is used for account-related purposes.
* **extendInfo:** (string) Additional metadata or extended configuration data in string format.

The response will include the following fields:

```json
{
		"code": 200, // (number: response code)
		"msg": "SUCCESS",	// (string: message)
		"data": { // (object: template fields)
				"id": 120, // (number: payment ID)
				"paymentName": "Wire (CPN)", // (string: payment name)
				"paymentType": 5,	 // (string: payment type)
				"trench": "Circle Payment Network", //(string: trench)
				"fieldList": [{						  //(list: List of original field information)
						"index": 1, 
						"indexCode": "beneficiaryName", 
						"textType": 4, 
						"title": "Beneficiary Name", 
						"promptText": "Please enter Beneficiary Name", 
						"minLimit": 1, 
						"maxLimit": 300,
						"isOptional": false,
						"isAccount": false, 
						"extendInfo": ""
					}, {
						"index": 2,
						"indexCode": "country",
						"textType": 6,
						"title": "Nationality",
						"promptText": "Please select Nationality",
						"minLimit": 1,
						"maxLimit": 300,
						"isOptional": false,
						"isAccount": false,
						"extendInfo": ""
					}, {
						"index": 3,
						"indexCode": "dateOfBirth",
						"textType": 9,
						"title": "Date of Birth / Date of Incorporation",
						"promptText": "Please enter Date of Birth / Date of Incorporation (yyyy-MM-dd)",
						"minLimit": 1,
						"maxLimit": 10,
						"isOptional": true,
						"isAccount": false,
						"extendInfo": ""
					}, {
						"index": 13,
						"indexCode": "useCase",
						"textType": 10,
						"title": "Use Case",
						"promptText": "Please select Use Case",
						"minLimit": 1,
						"maxLimit": 100,
						"isOptional": false,
						"isAccount": false,
						"extendInfo": "[{\"code\":\"B2B\",\"name\":\"B2B\"},{\"code\":\"B2C\",\"name\":\"B2C\"}]"
					}, {
						"index": 24,
						"indexCode": "accountNumber",
						"textType": 4,
						"title": "Account Number",
						"promptText": "Please enter Account Number",
						"minLimit": 1,
						"maxLimit": 34,
						"isOptional": false,
						"isAccount": true,
						"extendInfo": ""
					}]
		}
}
```
