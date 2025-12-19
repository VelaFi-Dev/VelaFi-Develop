---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/api-reference/basic-configuration/upload-file
---

# Upload File

This API allows you to upload invoices for a specific merchant kyc/kyb file.



Request Header: `X-BH-TOKEN: ******`

* Request Header: `Content-Type: multipart/form-data`
* Request Method: `POST`
* Request Path: `/v2/base/file/upload`
* Authorization: Required



Form **Parameters**

* **businessType**: (Required, string) The type of business is currently fixed as FIAT\_ACCOUNT
* **files**: (Required, file) Upload multiple files. The maximum number of uploaded files is 5, with each file range (min 10KB - max 3M). Supported formats are \[jpg, png, jpeg, pdf].



**Response Structure**The response will include the following fields:

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": [
        {
            "fileName": "id-front.jpg", //The original name of the file
            "fileType": "jpg", //The type of the document
            "fileUrl": "1172300499489225472/f97d9f9b-641a-4245-8d99-aa4788015e38.jpg", //Relative file path
            "tempFileUrl": "https://chats-images-files.s3.ap.amazonaws.com/8d99-aa4788015e38.jpg?x-amz-security-token=IQoJb3JpZ2luX2VjE" //Temporary file path check
        }
    ]
}
```



**Notes**

* Ensure that valid authorization tokens are included in the request headers for successful execution.
* Check that the uploaded files meet the specified requirements (number, size, and format).
