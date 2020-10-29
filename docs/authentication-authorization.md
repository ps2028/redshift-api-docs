###### [Home](README.md) • [Endpoints](/endpoints/README.md) • [Authentication and Authorization](/authentication-authorization.md) • [Script](/script.md)
---

# Authentication and Authorization
### Authentication Token
```
define("cipherMethod", "aes-128-cbc");
define("key", "5rCBIs9Km!!cacr1");
define("iv", "123hasdba036vpax");

// Token format: <email>:<hashedpassword_stored_inside_db>:<randomchars>
$plaintext = "email:password:randomchars"
$token = openssl_encrypt($plaintext, cipherMethod, key, $options = 0, iv);

echo $token;
```

### Levels
* Guest - Can perform only single calculation per request, result returned directly as a response.
* Registered user
    * General User - Can perform multiple calculations per request, results are stored into the database, and can retrieved anytime using the `/result` endpoint.
    * Admin - Enjoys same rights as General, additionally can fetch status and result for any calculation. Get system-load of the server.

### Note
* job_id is the realationship between a calculation and a user, this wasn't necessary from our standpoint, but it was implemented on the request of the front-end team. *
