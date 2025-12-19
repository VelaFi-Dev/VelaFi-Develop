---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/api-reference/order/upload-invoice-documents-for-a-specific-order
---

# Upload Invoice Documents For a Specific Order

This API allows you to upload invoices for a specific order.

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Header**: `Content-Type: multipart/form-data`
* **Request Method**: `POST`
* **Request Path**: `v2/order/invoice`
* **Authorization**: Required

Form **Parameters**

* **orderId**: (number) The ID of the order for which the invoice is being uploaded.
* **files**: (file) Upload multiple files. The maximum number of uploaded files is 5, with each file limited to 5 MB in size. Supported formats are \[jpg, png, jpeg, pdf].

**Response Structure**

The response will include the following fields:

* **code:** (number)  response code
* **msg**: (string) message
* data: (boolean) indicates if the confirmation was successful

```json
{
    "code": 200,        
    "msg": "SUCCESS",
    "data": true 
}

```

#### Notes

* Ensure that valid authorization tokens are included in the request headers for successful execution.
* Check that the uploaded files meet the specified requirements (number, size, and format).
