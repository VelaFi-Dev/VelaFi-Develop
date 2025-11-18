---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/webhooks/webhook-setup
---

# Webhook Setup

**Receiving Webhook Events**

TruBit Business API will send webhooks to your designated URL as a HTTP POST request with a JSON payload. You can provide your URLs via the webhook subscription endpoint, and retrieve, modify, or delete later them as you wish.

**Validation**

TruBit Business signs the webhook payload that is sent to your endpoint, and you can validate it by verifying the `signature` attached in the request header:

1. Extract the `signature` from the header, uses hexadecimal encoding.
2. Compute the hash with `RSA-SHA256` using the payload and the public key.
3. Compare the hash with the reap-signature and make sure they match.



**For Java Code**

```java
import java.security.*;
import java.security.spec.X509EncodedKeySpec;
import java.util.Base64;
import javax.servlet.http.HttpServletRequest;

public class CallbackController {

    //Place your public key according to the environment
    private String publicKey = "PUBLIC KEY";

    public String callbackNotice(HttpServletRequest request, @RequestBody String param) {
        //extract the signature
        String signature = request.getHeader("signature");
    
        //Use RSA-SHA256 to verify the signature, This signature uses hexadecimal encoding.
        boolean verified = verifyRSASHA256(param, signature, publicKey);
        System.out.println(String.format("verified:%s", verified));
    
        return String.format("{\"callbackStatus\":\"%s\"}", (verified ? "SUCCESS" : "FAIL"));  
    }
    
    public static boolean verifyRSASHA256(String data, String signature, String publicKeyStr) {
        try {
            // 1. Decode the Base64-encoded public key
            byte[] publicKeyBytes = Base64.getDecoder().decode(publicKeyStr);
            X509EncodedKeySpec keySpec = new X509EncodedKeySpec(publicKeyBytes);  
                      
            // 2. Generate RSA public key
            KeyFactory keyFactory = KeyFactory.getInstance("RSA");
            PublicKey publicKey = keyFactory.generatePublic(keySpec);
                        
            // 3. Initialize Signature object
            Signature sig = Signature.getInstance("SHA256withRSA");
            sig.initVerify(publicKey);
            
            // 4. Update the data to be verified
            sig.update(data.getBytes("UTF-8"));
            
            // 5. Decode the hexadecimal encoding signature
            byte[] signatureBytes = decodeHex(signature);
            
            // 6. Verify the signature
            return sig.verify(signatureBytes);
        } catch (Exception e) {
            e.printStackTrace();
            return false;
        }
    }
    
    public static byte[] decodeHex(String value) {
        int len = value.length();
        byte[] data = new byte[len / 2];

        for (int i = 0; i < len; i += 2) {
            data[i / 2] = (byte) ((Character.digit(value.charAt(i), 16) << 4)
                    + Character.digit(value.charAt(i+1), 16));
        }
        return data;
    }
    
}
```

**For Python Code**

```python
import json
from flask import request

# Place your public key according to the environment
public_key = "PUBLIC KEY"

def callback_notice():
    # Extract the parameter and signature
    param = request.get_data(as_text=True)
    signature = request.headers.get('signature')
    
    # Use RSA-SHA256 to verify the signature, This signature uses hexadecimal encoding.
    # Note: You'll need to implement or import a similar verify function
    verified = sha256_rsa_verify(param, signature, public_key)
    print(f"verified:{verified}")
    
    return json.dumps({"callbackStatus": "SUCCESS" if verified else "FAIL"})
    
def sha256_rsa_verify(data, signature, public_key):
    """
    Verify RSA-SHA256 signature
    :param data: The data that was signed
    :param signature: The signature to verify
    :param public_key: The public key to use for verification
    :return: Boolean indicating if verification succeeded
    """
    pass
```

**For JavaScript Code**

```javascript
// Place your public key according to the environment
const publicKey = "PUBLIC KEY";

async function callbackNotice(req, param) {
    // Extract the signature
    const signature = req.headers['signature'];

    // Use RSA-SHA256 to verify the signature, This signature uses hexadecimal encoding.
    const verified = await verifyRSASHA256(param, signature, publicKey);
    console.log(`verified: ${verified}`);

    return JSON.stringify({
        callbackStatus: verified ? "SUCCESS" : "FAIL"
    });
}

// RSA-SHA256 verification function (example using crypto module)
async function verifyRSASHA256(data, signature, publicKey) {
    const crypto = require('crypto');
    const verify = crypto.createVerify('RSA-SHA256');
    verify.update(data);
    return verify.verify(publicKey, signature, 'base64');
}
```
