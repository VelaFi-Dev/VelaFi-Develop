---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/payment-method/get-payment-templates
---

# Get Payment Templates

#### Get Payment Method Templates

This API retrieves the template details for various payment methods based on the provided payment method ID.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Method**: `GET`
* **Request Path**: `/v2/payments/templates`
* **Authorization Required**: Yes

#### Query Parameters

* **paymentId**: (int) The ID of the payment method.

#### Authorization

This request requires authorization.

#### Payment ID Lists

| Payment ID | Name                                | Type      |
| ---------- | ----------------------------------- | --------- |
| 58         | Automated SPEI - Arcus              | Automatic |
| 105        | SPEI - FINCO PAY                    | Automatic |
| 63         | Automated Bank Transfer (Argentina) | Automatic |
| 68         | PSE/ACH                             | Automatic |
| 77         | SWIFT (HK)                          | Automatic |
| 78         | CHATS                               | Automatic |
| 79         | FPS                                 | Automatic |
| 81         | ACH\_push                           | Automatic |
| 82         | ACH\_Virtual Account                | Automatic |
| 83         | WIRE                                | Automatic |
| 84         | WIRE\_Virtual Account               | Automatic |
| 90         | Automated Pix                       | Automatic |
| 95         | Automated Bank Transfer(Peru)       | Automatic |
| 111        | ACH Account\_Cross River Bank       | Automatic |
| 113        | WIRE Account\_Cross River Bank      | Automatic |
| 115        | SWIFT Account\_Cross River Bank     | Automatic |
| 19         | Pix                                 | Manual    |
| 27         | Bank Transfer (Brazil)              | Manual    |
| 28         | Bank Transfer (Argentina)           | Manual    |
| 29         | Manual Bank Transfer (Mexico)       | Manual    |
| 36         | Mercantil                           | Manual    |
| 37         | Bank Transfer (Venezuela)           | Manual    |
| 38         | Banco De Venezuela                  | Manual    |
| 39         | Ubii Pagos                          | Manual    |
| 40         | Banesco                             | Manual    |
| 41         | Pago Movil                          | Manual    |
| 42         | BNC Banco National De Credito       | Manual    |
| 43         | BBVA Provincial (Venezuela)         | Manual    |
| 44         | Bancamiga                           | Manual    |
| 45         | Bancaribe                           | Manual    |
| 46         | Banplus                             | Manual    |
| 47         | Banco Activo                        | Manual    |
| 48         | Bank Transfer (Colombia)            | Manual    |
| 51         | 境內銀行轉賬 (台灣)                         | Manual    |
| 52         | 街口轉賬                                | Manual    |
| 53         | LINE Pay                            | Manual    |
| 59         | Bank Transfer (Perú)                | Manual    |
| 60         | Bank Transfer (Chile)               | Manual    |
| 61         | Manual USD Payments (CHATS)         | Manual    |
| 64         | Banque Msr UAE                      | Manual    |
| 67         | Bank Transfer (Uruguay)             | Manual    |

#### Response Structure

The response will include the following fields:

```json
{
    "code": 0,                            // (number: response code)
    "msg": "",                            // (string: message)
    "data": {                             // (object: template fields)
        [string]: [string]                // (key-value pairs of template fields)
    }
}
```

#### Example Responses

**Example:**

**Mexico Bank (58: Automated SPEI - Arcus)**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "CLABE number": "",
        "Account number/card": "",
        "Beneficiary Name": ""
    }
}
```

**Mexico Bank (105: SPEI - FINCO PAY)**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "Account Type": "",
	"Account Number": "",
	"Beneficiary Name": "",
	"Bank Code": ""     
    }
}

Account Type: enum [clabe: VA account, debit: card account]
Bank Code: Bank code is required to be filled in only when the account type is "debit". See Mexico FINCO PAY Bank Codes.
```

**Argentina Bank (63: Automated Bank Transfer (Argentina))**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "CVU number": "",
        "cuit": "",
        "Bank name": ""
    }
}
```

**SEPA (Payment Type 2)**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "Bank Name": "",
        "Account Owner Name": "",
        "Account Owner Type": "",
        "Bank Country/Region": "",
        "Account Number": "",
        "Bic": "",
        "firstName": "",
        "lastName": "",
        "businessName": ""
    }
}
Account Owner Type must be either Business or Individual.
If Account Owner Type is Business, businessName is required.
If Account Owner Type is Individual, firstName and lastName are required.

Bank Country/Region is ISO 3166-1
```

**WIRE/ACH/SWIFT (ES) (Payment Type 2)**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "Bank Name": "",
        "Account Owner Name": "",
        "Account Owner Type": "",
        "Bank Country/Region": "",
        "Account Number": "",
        "Routing Number": "",
        "Street Line1": "",
        "Street Line2": "",
        "City": "",
        "State": "",
        "Postal Code": "",
        "firstName": "",
        "lastName": "",
        "businessName": ""
    }
}
Account Owner Type must be either Business or Individual.
If Account Owner Type is Business, businessName is required.
If Account Owner Type is Individual, firstName and lastName are required.

Bank Country/Region is ISO 3166-1
State is ISO 3166-2
```

**SWIFT (HK) / CHATS (Payment Type 3)**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "Account Owner Type": "",
        "IBAN": "",
        "Bank Name": "",
        "Bank Country/Region": "",
        "Bank Identifier": "",
        "Street": "",
        "City": "",
        "State": "",
        "Country/Region": "",
        "Postal Code": ""
        "firstName": "",
        "lastName": "",
        "businessName": ""
    }
}

Account Owner Type must be either Business or Individual.
If Account Owner Type is Business, businessName is required.
If Account Owner Type is Individual, firstName and lastName are required.

Bank Country/Region is ISO 3166-1

```

**Colombia Bank (68: PSE/ACH)**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "Account Type": "",
        "Full Name": "",
        "ID Document Type": "",
        "ID Document Number": "", 
        "Bank Code": "",
        "Bank Account Number": ""
    }
}

Account Type: enum [cc: Checking Account, ch: Savings Account, dp:Electronic deposit]
ID Document Type: enum [cc: Citizenship ID, nit: Tax Identification Number, ce: Foreigner ID,  pa: Pasaporte (Passport),  ppt: Temporary Protection Permit,  ti: Identity Card, rc: Civil Registry, te: Foreigner Card, die: Foreign Identification Document, nd: No Document]
Bank Code: See Colombian Bank Codes, The bank code filled in must be one that is supported by the corresponding Account Type.
```

**Brazil Bank (90: Automated Pix)**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "Pix Type": "",
        "Pix Key": ""
    }
}

Pix Type: enum [CPF:11 digits, CNPJ:14 digits, EMAIL:email, PHONE: 10-11 digits, RANDOM_KEY: with "-"]
```

**Peru Bank (95: Automated Bank Transfer(Peru))**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
       "Bank Name": "",
       "Account Type": "",
       "Account Number": "",
       "CCI Number": "",
       "Email": "",
       "Identification Type": "",
       "Identification Number": "",
       "Name": "",
       "Phone Number": ""
    }
}
```

## Colombia Bank Codes <a href="#colombian-bank-codes" id="colombian-bank-codes"></a>

<table><thead><tr><th width="98">Code</th><th width="474">Bank</th><th width="204">Type</th></tr></thead><tbody><tr><td>1001</td><td>BANCO DE BOGOTA</td><td>cc, ch, dp</td></tr><tr><td>1002</td><td>BANCO POPULAR</td><td>cc, ch, dp</td></tr><tr><td>1006</td><td>ITAU</td><td>cc, ch</td></tr><tr><td>1007</td><td>BANCOLOMBIA</td><td>cc, ch, dp</td></tr><tr><td>1009</td><td>CITIBANK</td><td>cc, ch</td></tr><tr><td>1012</td><td>BANCO GNB SUDAMERIS</td><td>cc, ch</td></tr><tr><td>1013</td><td>BBVA COLOMBIA</td><td>cc, ch, dp</td></tr><tr><td>1019</td><td>SCOTIABANK COLPATRIA S.A</td><td>cc, ch</td></tr><tr><td>1023</td><td>BANCO DE OCCIDENTE</td><td>cc, ch</td></tr><tr><td>1032</td><td>BANCO CAJA SOCIAL BCSC SA</td><td>cc, ch</td></tr><tr><td>1040</td><td>BANCO AGRARIO</td><td>cc, ch, dp</td></tr><tr><td>1047</td><td>BANCO MUNDO MUJER</td><td>ch</td></tr><tr><td>1051</td><td>BANCO DAVIVIENDA SA</td><td>cc, ch, dp</td></tr><tr><td>1052</td><td>BANCO AV VILLAS</td><td>cc, ch, dp</td></tr><tr><td>1053</td><td>BANCO W</td><td>cc, ch</td></tr><tr><td>1059</td><td>BANCO DE LAS MICROFINANZAS - BANCAMIA S.A.</td><td>cc, ch</td></tr><tr><td>1060</td><td>BANCO PICHINCHA</td><td>cc, ch</td></tr><tr><td>1061</td><td>BANCOOMEVA</td><td>cc, ch, dp</td></tr><tr><td>1062</td><td>BANCO FALABELLA S.A.</td><td>cc, ch</td></tr><tr><td>1063</td><td>BANCO FINANDINA S.A.</td><td>cc, ch</td></tr><tr><td>1065</td><td>BANCO SANTANDER DE NEGOCIOS COLOMBIA S.A</td><td>ch</td></tr><tr><td>1066</td><td>BANCO COOPERATIVO COOPCENTRAL</td><td>cc, ch, dp</td></tr><tr><td>1067</td><td>MIBANCO S.A.</td><td>cc, ch, dp</td></tr><tr><td>1069</td><td>BANCO SERFINANZA S.A</td><td>cc, ch, dp</td></tr><tr><td>1070</td><td>LULO BANK S.A.</td><td>ch</td></tr><tr><td>1071</td><td>BANCO J.P. MORGAN COLOMBIA S.A.</td><td>cc, ch</td></tr><tr><td>1097</td><td>Dale</td><td>dp</td></tr><tr><td>1121</td><td>FINANCIERA JURISCOOP S.A. COMPAÑIA DE FINANCIAMIENTO</td><td>ch</td></tr><tr><td>1283</td><td>COOPERATIVA FINANCIERA DE ANTIOQUIA</td><td>ch, dp</td></tr><tr><td>1286</td><td>JFK COOPERATIVA FINANCIERA</td><td>ch</td></tr><tr><td>1289</td><td>COOTRAFA COOPERATIVA FINANCIERA</td><td>ch</td></tr><tr><td>1292</td><td>CONFIAR COOPERATIVA FINANCIERA</td><td>ch</td></tr><tr><td>1303</td><td>BANCO UNION S.A</td><td>ch</td></tr><tr><td>1370</td><td>COLTEFINANCIERA S.A</td><td>ch</td></tr><tr><td>1507</td><td>NEQUI</td><td>ch, dp</td></tr><tr><td>1551</td><td>DAVIPLATA</td><td>dp</td></tr><tr><td>1558</td><td>BAN100 S.A</td><td>cc, ch</td></tr><tr><td>1637</td><td>IRIS</td><td>ch</td></tr><tr><td>1801</td><td>MOVII</td><td>dp</td></tr><tr><td>1802</td><td>DING TECNIPAGOS SA</td><td>dp</td></tr><tr><td>1803</td><td>POWWI</td><td>dp</td></tr><tr><td>1804</td><td>UALA</td><td>ch</td></tr><tr><td>1805</td><td>BANCO BTG PACTUAL</td><td>cc</td></tr><tr><td>1808</td><td>BOLD CF</td><td>dp</td></tr><tr><td>1809</td><td>NU COLOMBIA</td><td>ch</td></tr><tr><td>1811</td><td>RAPPIPAY</td><td>ch, dp</td></tr><tr><td>1812</td><td>COINK</td><td>dp</td></tr><tr><td>1814</td><td>GLOBAL66</td><td>dp</td></tr><tr><td>1815</td><td>Alianza fiduciaria</td><td>ch</td></tr><tr><td>1816</td><td>Crezcamos</td><td>cc, ch</td></tr></tbody></table>

## Peru Bank Codes

<table><thead><tr><th width="98">Code</th><th width="691">Bank</th></tr></thead><tbody><tr><td>01</td><td>BCP</td></tr><tr><td>02</td><td>Interbank</td></tr><tr><td>03</td><td>BBVA</td></tr><tr><td>04</td><td>Scotiabank</td></tr><tr><td>05</td><td>Banco de Comercio</td></tr><tr><td>06</td><td>BanBif (Banco Interamericano de Finanzas)</td></tr><tr><td>07</td><td>Banco Pichincha</td></tr><tr><td>08</td><td>Citibank</td></tr><tr><td>09</td><td>Banco GNB</td></tr><tr><td>10</td><td>Banco Santander</td></tr><tr><td>11</td><td>Banco Azteca</td></tr><tr><td>12</td><td>Banco Cencosud</td></tr><tr><td>13</td><td>ICBC PERU BANK</td></tr><tr><td>14</td><td>Banco de la Nación</td></tr><tr><td>15</td><td>Caja Cusco</td></tr><tr><td>16</td><td>Caja Huancayo</td></tr><tr><td>17</td><td>Caja Maynas</td></tr><tr><td>18</td><td>Caja Metropolitana</td></tr><tr><td>19</td><td>Caja Municipal Ica</td></tr><tr><td>20</td><td>Caja Sullana</td></tr><tr><td>21</td><td>Caja Tacna</td></tr><tr><td>22</td><td>Caja Trujillo</td></tr></tbody></table>

## Mexico FINCO PAY Bank Codes

<table><thead><tr><th width="442">Code</th><th width="400">Bank</th></tr></thead><tbody><tr><td>14b392f6-5dd9-4cd9-ac51-d13c5547c137</td><td>FINCO_PAY</td></tr><tr><td>99d3c26a-bf2c-494e-9a39-c3359a692c38</td><td>ALBO</td></tr><tr><td>1d792ab5-95f3-44ba-944f-9da198f68c2e</td><td>CASHI</td></tr><tr><td>af8250bd-f169-480f-9dc5-0fafeb89c21b</td><td>KAPITAL</td></tr><tr><td>05409c64-a872-4e5e-9bac-c2a16261aea1</td><td>NAFIN</td></tr><tr><td>6ec6bbd5-94fa-47c4-a2c6-8ed8c3f3457b</td><td>HIPOTECARIAFED</td></tr><tr><td>8e04b055-b6cf-4e66-abfb-fc845d69a1bc</td><td>ACCENDOBANCO</td></tr><tr><td>810c88e2-8fdb-4ecd-9747-eda708b5ebe7</td><td>AMERICANEXPRES</td></tr><tr><td>2218cd20-0fdf-4f81-ab5c-90587b91057a</td><td>BANKOFAMERICA</td></tr><tr><td>6bb38026-7386-4992-8fdf-946b17b1d16c</td><td>MUFG</td></tr><tr><td>c4d942d0-c102-48ef-9756-532266183856</td><td>JPMORGAN</td></tr><tr><td>9d989796-0be4-4466-a213-61a27cdfcfaf</td><td>BMONEX</td></tr><tr><td>b9eae957-344c-4169-8c41-e189d3f2c74a</td><td>VEPORMAS</td></tr><tr><td>b2438e53-33bd-456e-937a-24e59b65fb35</td><td>DEUTSCHE</td></tr><tr><td>fe025a91-37ea-4869-bd68-687fd63ab6a3</td><td>CREDITSUISSE</td></tr><tr><td>a832542e-5eb2-49ae-b01e-b441f0d4d1ec</td><td>AZTECA</td></tr><tr><td>b835e788-b8c0-497a-9ce2-f5dfeac607bd</td><td>BARCLAYS</td></tr><tr><td>ef51659d-6b84-4f29-a92e-e435648be5b5</td><td>COMPARTAMOS</td></tr><tr><td>fc9a2874-2a07-416b-ac97-cf0d8eb68101</td><td>MULTIVABANCO</td></tr><tr><td>a72ff745-6094-4fb0-96ae-ea86847cf9b7</td><td>ACTINVER</td></tr><tr><td>5dcd3410-a88a-4c7a-8c4f-390f666836f4</td><td>INTERCAMBANCO</td></tr><tr><td>a4f9d274-2407-4295-8136-ccd0135192d7</td><td>BANCOPPEL</td></tr><tr><td>522333da-cff6-40b9-943e-71da34879815</td><td>ABCCAPITAL</td></tr><tr><td>ce134175-ad5d-4a6b-b429-deb0f4040166</td><td>CONSUBANCO</td></tr><tr><td>4583c80e-f7ad-4d62-bc2f-09b1aab598b9</td><td>VOLKSWAGEN</td></tr><tr><td>e10fb312-0538-48f6-ab9a-fc0184563d37</td><td>CIBANCO</td></tr><tr><td>92acfe76-0a74-4817-83e1-3fdabe2cc89c</td><td>BBASE</td></tr><tr><td>505292b9-41bc-4cf8-8765-1fb75fc0a264</td><td>BANKAOOL</td></tr><tr><td>d2ea27c8-0b41-4ca8-b5f4-e62f97d46909</td><td>PAGATODO</td></tr><tr><td>082a3ea6-12a9-42ce-9716-59d98e080a0e</td><td>INMOBILIARIO</td></tr><tr><td>95d541a3-9000-4d43-a3b2-be3dc08e5964</td><td>DONDE</td></tr><tr><td>13f54258-ae13-4d1d-b470-113c66db84f6</td><td>BANCREA</td></tr><tr><td>50b78495-f60b-475c-be1d-5f31588f9a1b</td><td>PROGRESO</td></tr><tr><td>688d032b-fc6f-43b7-97a1-e75a5b718597</td><td>BANCOFINTERRA</td></tr><tr><td>a27f9214-00d4-4826-8e59-832daf7f41aa</td><td>ICBC</td></tr><tr><td>0eff7474-046f-4ea7-9cdf-4ef56427919b</td><td>SABADELL</td></tr><tr><td>5e80e573-7e55-474f-80e0-b2424713b2a1</td><td>BANXICO</td></tr><tr><td>a12c354f-d2e0-462f-8b95-49d08a5aa376</td><td>BANCOMEXT</td></tr><tr><td>04a2c4e7-2e1c-4235-bb0b-599215f60560</td><td>BANOBRAS</td></tr><tr><td>cc1cdae0-3091-40b7-80af-681fdf6a9bfd</td><td>BANAMEX</td></tr><tr><td>6fe813b9-3daf-4fc4-9398-82dc75e26cd0</td><td>BaBien</td></tr><tr><td>e01d0e74-c95e-4cfd-89bb-e664bf86e4f3</td><td>SHINHAN</td></tr><tr><td>3387b78c-92a2-4636-94d3-a949dcbabd00</td><td>MIZUHOBANK</td></tr><tr><td>4b25af05-9f6f-4d5e-aaa8-5cce5059c280</td><td>BANKOFCHINA</td></tr><tr><td>368ad8e9-5f7a-49c5-93b3-be799dadacd8</td><td>BANCOS</td></tr><tr><td>9ded667d-ad5c-4da8-aa85-acf56a14adb7</td><td>NU_MEXICO</td></tr><tr><td>2ab903aa-e32c-4e40-a811-684050fd5476</td><td>FOMPED</td></tr><tr><td>d94ebc8d-6675-4158-8dca-0937b0cff6b9</td><td>MONEXCB</td></tr><tr><td>ead338fc-35c6-4436-b062-b87df217a152</td><td>GBM</td></tr><tr><td>4354277f-e083-48ff-981f-24dae6124027</td><td>MASARI</td></tr><tr><td>af3a5d5d-b052-4e73-8411-69db92cab98d</td><td>VALUE</td></tr><tr><td>10997d0a-3ac5-494d-80b5-cede1f6cc2e4</td><td>ESTRUCTURADORES</td></tr><tr><td>728550ff-2c76-4cbf-8969-e488081ecdfe</td><td>VECTOR</td></tr><tr><td>7cbc1932-b402-406f-82e7-39ddc41246d9</td><td>MULTIVACBOLSA</td></tr><tr><td>4cb562f8-0a9a-4df5-8451-d01a971a2944</td><td>FINAMEX</td></tr><tr><td>8cf9ad29-b0db-40a5-82f4-7e3e19af8400</td><td>VALMEX</td></tr><tr><td>4c469adf-4e07-4a3b-8ea2-955e69516e88</td><td>PROFUTURO</td></tr><tr><td>a930ac56-0d84-4ca5-9340-8cf3ff93de7f</td><td>CBINTERCAM</td></tr><tr><td>4b62d90c-8db7-4d50-a229-265786a643f0</td><td>CIBOLSA</td></tr><tr><td>52c1e083-309e-4bb8-ba1f-779b6493a9ce</td><td>FINCOMUN</td></tr><tr><td>15d56a15-86a9-48a0-8222-34c9b482cd29</td><td>HDISEGUROS</td></tr><tr><td>fd852c62-0ebc-470b-a9dc-bdc2d71b174e</td><td>REFORMA</td></tr><tr><td>033f8743-3bc4-45d7-8bc9-7805ccedb2f9</td><td>STP</td></tr><tr><td>0a01916c-e09d-4834-84bd-35ce27de404f</td><td>EVERCORE</td></tr><tr><td>6dad109e-5163-49d2-8557-7af8b35cad2b</td><td>CREDICAPITAL</td></tr><tr><td>8c9f8509-2989-4a97-aeee-bc55bdea330e</td><td>KUSPIT</td></tr><tr><td>163a12e4-e463-45cc-a684-7f986d5f1fae</td><td>UNAGRA</td></tr><tr><td>4e18dd45-d4a4-491b-af9e-cb086c69f4c2</td><td>ASPINTEGRAOPC</td></tr><tr><td>97bce569-8fc0-4025-9c04-9860592f77fd</td><td>LIBERTAD</td></tr><tr><td>ea38aef5-dbe0-42ec-8870-6844cf77ba30</td><td>C.B.INBURSA</td></tr><tr><td>16a4f525-ef02-4018-b0ef-88a98530c2c8</td><td>CAJAPOPMEXICA</td></tr><tr><td>a03aa6d1-0aa2-48ad-8b7d-b4dfeeed51cb</td><td>CRISTOBALCOLON</td></tr><tr><td>2459cecf-7841-4cf1-a98a-af9bf6984f92</td><td>CAJATELEFONIST</td></tr><tr><td>c9bff5ba-8f00-4743-83ec-f62af901a1d9</td><td>TRANSFER</td></tr><tr><td>0f0ab913-cfdb-4b11-b0c7-4c2b2bac9024</td><td>FONDO(FIRA</td></tr><tr><td>31e3cec1-d95c-4849-92ff-36c9944f91cc</td><td>CREDICLUB</td></tr><tr><td>d028742d-5cbe-4add-8518-718b840d023a</td><td>XXI-BANORTE</td></tr><tr><td>429d2ddc-e369-4438-a393-dbfb44e4d635</td><td>TECREEMOS</td></tr><tr><td>55196e15-c27f-40cd-a824-c28fdc0ed49a</td><td>SCPROMYOP</td></tr><tr><td>7dbf5a21-9dfd-4a71-8dd5-7832681dd6a0</td><td>CAPITALACTIVO</td></tr><tr><td>cf3d6099-5bdd-4738-b3a5-2bf7f127d33e</td><td>BURSAMETRICA</td></tr><tr><td>48a881e1-95ab-44bb-9f69-fd1ae6ade6ad</td><td>ARCUS</td></tr><tr><td>0b0e321e-fd89-4af9-a5c9-e3f030874646</td><td>FND</td></tr><tr><td>71db3f6f-0da8-4455-8e6f-1caea04223c0</td><td>CLSBANK</td></tr><tr><td>86107256-75dc-4429-ba6c-de5ae71e75fb</td><td>INDEVAL</td></tr><tr><td>5e02554c-4471-4d21-9f6e-5c7b0d754443</td><td>BanCobro_R</td></tr><tr><td>b9133baa-8e87-4162-bcf9-223ec4d297a5</td><td>BanCobro</td></tr><tr><td>481bdbde-7e47-43d9-8a30-bdd0968c40b1</td><td>BanCobro</td></tr><tr><td>e1adef4c-5368-41bb-92f2-7dc6ec2a6465</td><td>Validador</td></tr><tr><td>912f9702-f480-4f10-acec-788119e01d88</td><td>BANAMEX</td></tr><tr><td>e4e7f75c-4f61-4bce-b411-a5509347d755</td><td>BBVABANCOMER</td></tr><tr><td>0997b675-5230-4752-ae14-cff991d9f6c3</td><td>SANTANDER</td></tr><tr><td>89bfe0b7-ccd2-4f2d-93ef-472a62a1da45</td><td>HSBC</td></tr><tr><td>ec7f37e2-4a5d-4df7-9a0d-17200497a603</td><td>BANORTE</td></tr><tr><td>daa62e35-19e4-4b39-a99c-2ea611cf0476</td><td>AZTECA</td></tr><tr><td>67ee7fff-258f-4bd6-888c-7ff4d4c2477a</td><td>BANJERCITO</td></tr><tr><td>5ad49c1d-bff3-4b00-8bc5-32df6cb1cd2c</td><td>BBVABANCOMER</td></tr><tr><td>93e25084-52b2-4c4e-bfd3-39b531f9fae1</td><td>SANTANDER</td></tr><tr><td>1aa2cc10-84ba-453e-adae-9edcd9232847</td><td>HSBC</td></tr><tr><td>bbc556be-0cae-4907-aff8-9851774949f3</td><td>BAJIO</td></tr><tr><td>538aeb53-f5f7-4eea-9747-035c6fc80e3a</td><td>INBURSA</td></tr><tr><td>bdb58e56-a7d4-4fcd-b32c-ed780a9a23d0</td><td>MIFEL</td></tr><tr><td>631b3a6a-71fc-43dc-a483-7ea6ca46a7ed</td><td>SCOTIABANK</td></tr><tr><td>a9151de7-393f-4ea1-a897-92dd158f3e25</td><td>BANREGIO</td></tr><tr><td>2ef06d9b-0739-40fe-81c2-4a88bdd7e939</td><td>INVEX</td></tr><tr><td>9bdd8ac7-b628-41c7-b93a-123d09378878</td><td>BANSI</td></tr><tr><td>223ae9ee-47ff-4b4f-a48d-60f1c9893dfe</td><td>AFIRME</td></tr><tr><td>1ffb6b3b-1e93-407a-b5ec-cbb1139c1898</td><td>BANORTE</td></tr><tr><td>d3f867b9-9f59-46f8-b937-050d30d311bb</td><td>FONDEADORA</td></tr><tr><td>f34c6d1c-5204-41a4-adc0-7440cd1e8ea9</td><td>TESORED</td></tr><tr><td>cdf6384e-a8bc-423a-b42a-b7b488aeee83</td><td>NVIO</td></tr><tr><td>5d4208e6-8c5b-4654-a98a-5e35fef74c2b</td><td>MERCADO_PAGO_W</td></tr><tr><td>e96d092b-cc4e-4602-8665-d91bed1210f1</td><td>CUENCA</td></tr><tr><td>23eafe0c-833c-41ff-89c3-5dfefbe376fd</td><td>SPIN_BY_OXXO</td></tr><tr><td>84e4e446-f7ed-4551-9360-ad39e5a2bf06</td><td>KLAR</td></tr></tbody></table>

#### Notes

* The `data` object contains key-value pairs representing the required fields for the specified payment method.
* Ensure that valid authorization tokens are included in the request headers for successful execution.
