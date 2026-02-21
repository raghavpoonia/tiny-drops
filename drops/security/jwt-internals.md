# JWT Internals

**Category**: `security`  
**Difficulty**: `3`  
**Read Time**: `60s`  
**Tags**: #auth #tokens #cryptography

---

## What
JSON Web Token - self-contained auth token with header, payload, signature.

## Why It Exists
Stateless authentication. Server doesn't store sessions - just validates signature. Scales horizontally.

## How It Works
1. **Header**: Algorithm (HS256, RS256) + token type
2. **Payload**: Claims (user ID, expiry, roles)
3. **Signature**: HMAC/RSA signature of header + payload
4. Format: `base64(header).base64(payload).signature`

## Code
```python
import jwt, time

payload = {
    'user_id': 12345,
    'exp': int(time.time()) + 3600,
    'roles': ['user', 'admin']
}

token = jwt.encode(payload, 'secret-key', algorithm='HS256')

try:
    decoded = jwt.decode(token, 'secret-key', algorithms=['HS256'])
    print(decoded['user_id'])
except jwt.ExpiredSignatureError:
    print("Expired")
```

## The Gotcha
JWT is NOT encrypted - only BASE64 encoded. Anyone can decode the payload. NEVER put secrets in claims. Use HTTPS always.

No built-in revocation. If leaked, token valid until expiry. Mitigation: short expiry + refresh tokens.

## Real-World Example
OAuth 2.0, microservices auth, API gateways, SSO. IBM Cloud IAM uses JWT for service-to-service auth.

## Micro Challenge
Security difference between HS256 (HMAC) and RS256 (RSA) for JWT signing?

---

**Related**: []  
**Next**: [OAuth 2.0 Flow]
