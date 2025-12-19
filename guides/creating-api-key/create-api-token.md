---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/guides/creating-api-key/create-api-token
---

# Create API Token

This API allows you to generate a new API token for user authentication.

#### Endpoint Information

* **Request Method**: `GET`
* **Request Path**: `/v2/token/generate`
* **Authorization Required**: Yes

#### Request Headers

* `X-BH-APIKEY`: Your API key.

#### Query Parameters

* `timestamp`: The current time in milliseconds since the epoch.
* `signature`: The HMAC signature for the request.

#### Response Structure

The response will include the following fields:

```json
{
  "code": 200,                      // (number: response code)
  "msg": "SUCCESS",                 // (string: message)
  "data": {                         // (object: token details)
    "token": "09ef3523-6242-4a8d-80e2-24cfbdb35851", // (string: generated token)
    "expireTime": "1740568725231"  // (string: timestamp of the expiration time in milliseconds)
  }
}
```

#### Signature Generation Process

To generate the signature, follow these steps:

1. **Prepare the Message**: Create a string with the current timestamp: `"timestamp=1740568725231"`.
2. **Prepare the Key**: Use your `API_SECRET` as the key.
3. **Generate the Signature**: Use HMAC-SHA256 to create a hex string signature from the message and the key.

#### Example Code for Signature Generation

**Python**

```python
import time
import hmac
import hashlib

API_SECRET = "xxxx"
message = "timestamp=" + str(int(time.time() * 1000))
signature = hmac.new(API_SECRET.encode('utf-8'), message.encode('utf-8'), hashlib.sha256).hexdigest()

print("Signature:", signature)
```

**Java**

```java
import javax.crypto.Mac;
import javax.crypto.spec.SecretKeySpec;
import java.nio.charset.StandardCharsets;

public class Signature {
    public static void main(String[] args) throws Exception {
        String API_SECRET = "xxxx";
        String message = "timestamp=" + System.currentTimeMillis();
        String signature = hmacSHA256(API_SECRET, message);

        System.out.println("Signature: " + signature);
    }

    public static String hmacSHA256(String secret, String message) throws Exception {
        Mac sha256HMAC = Mac.getInstance("HmacSHA256");
        SecretKeySpec secretKey = new SecretKeySpec(secret.getBytes(StandardCharsets.UTF_8), "HmacSHA256");
        sha256HMAC.init(secretKey);
        byte[] bytes = sha256HMAC.doFinal(message.getBytes(StandardCharsets.UTF_8));
        return bytesToHex(bytes);
    }

    private static String bytesToHex(byte[] bytes) {
        StringBuilder sb = new StringBuilder();
        for (byte b : bytes) {
            sb.append(String.format("%02x", b));
        }
        return sb.toString();
    }
}
```

**JavaScript (Node.js)**

```javascript
const crypto = require('crypto');

const API_SECRET = 'xxxx';
const message = 'timestamp=' + Date.now();
const signature = crypto.createHmac('sha256', API_SECRET).update(message).digest('hex');

console.log('Signature:', signature);
```

**Go**

```go
package main

import (
    "crypto/hmac"
    "crypto/sha256"
    "encoding/hex"
    "fmt"
    "time"
)

func main() {
    API_SECRET := "xxxx"
    message := "timestamp=" + fmt.Sprint(time.Now().UnixNano()/1e6)
    signature := generateHMAC(API_SECRET, message)

    fmt.Println("Signature:", signature)
}

func generateHMAC(secret, message string) string {
    h := hmac.New(sha256.New, []byte(secret))
    h.Write([]byte(message))
    return hex.EncodeToString(h.Sum(nil))
}
```

**Rust**

```rust
use hmac::{Hmac, Mac};
use sha2::Sha256;
use std::time::{SystemTime, UNIX_EPOCH};

fn main() {
    let api_secret = "xxxx";
    let start = SystemTime::now();
    let since_the_epoch = start.duration_since(UNIX_EPOCH).expect("Time went backwards");
    let message = format!("timestamp={}", since_the_epoch.as_millis());
    let signature = generate_hmac(api_secret, &message);

    println!("Signature: {}", signature);
}

fn generate_hmac(secret: &str, message: &str) -> String {
    let mut mac = Hmac::<Sha256>::new_from_slice(secret.as_bytes()).expect("HMAC can take key of any size");
    mac.update(message.as_bytes());
    let result = mac.finalize();
    hex::encode(result.into_bytes())
}
```

#### Notes

* Ensure that you replace `"xxxx"` with your actual `API_SECRET`.
* The generated token will have an expiration time, which is provided in the response.
