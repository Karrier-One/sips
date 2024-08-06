| SIP-Number          |  |
| ---:                | :--- |
| Title               | Add Karrier One as a zkLogin OpenID provider |
| Description         | Add Karrier One as a whitelisted OpenID provider enabled for zkLogin on Sui. |
| Author              | Andrew Buchanan <abuchanan@karrier.one> |
| Editor              |  |
| Type                | Standard |
| Category            | Core |
| Created             | 2024-08-06 |
| Comments-URI        | |
| Status              | |
| Requires            | |


## Abstract

Currently no providers enabled on Sui support login with a phone number. Phone number logins are a dominant credential option in many sectors and having such a provider for zkLogin is crucial for mass adoption of zkLogin. Here we propose to add Karrier One as an OpenID provider on Sui that enables login with a phone number. This will allow applications in the sui ecosystem to onboard users to Sui seamlessly using simply a phone number.

## Motivation

zkLogin does not support any providers using phone number-based logins.  Many popular applications use phone number based accounts and/or logins today and adding a zkLogin provider that supports phone numbers will enable builders in the sui ecosystem to also use phone number based logins for creating wallets and interacting with dApps.

## Specification

Karrier One is hosting an openid provider built upon https://github.com/openiddict/openiddict-core which implements https://openid.net/specs/openid-connect-core-1_0.html and supports the code & implicit flows. TODO openiddict does support more flows if we want.


|             Item          | Endpoint  | Example Content | 
|-------------------------- |-----------|-----------------|
| Well known configuration  |    https://accounts.karrier.one/.well-known/openid-configuration       |                 |
| JWK endpoint              |    https://accounts.karrier.one/.well-known/jwks       |                 |
| Issuer                    |    https://accounts.karrier.one/   |                 |
| Authorization link          |   https://accounts.karrier.one/connect/authorize        |                 |
| Allowed Client IDs |    |     | 

#### JWK rotation details

TODO: Include discussion on JWK rotation frequency and policy here. 

#### JWK endpoint availability

TODO: Include discussion on what measures had been taken to ensure the JWK availability, i.e. status page to track liveness. 

#### Signing key storage details

TODO: Include the infra that you had implemented or used to ensure the certificate signing key is well managed and secure. 



## Rationale

TODO: Discuss the whys for rotation schedule and signing key storage options, any other alternatives considered and how you come to such a decision . 


## Backwards Compatibility

ZkLogin wallets are domain separated by the OpenID issuer and its client ID. There is no backward compatibility issue with existing issuers. 

Once this SIP is finalized with the configurations defined above (issuer string, client ID etc), they will not change again. Otherwise, the wallet created based on this configuration will result in loss of funds. 


## Test Cases

TODO: provide an example JWT token and parsed JWT token payload (using jwt.io) with nonce hTPpgF7XAKbW37rEUS6pEVZqmoI

TODO: Provide a long-live video clip of a complete login flow for testing and/or screenshots. 


## Reference Implementation

N/A. To be implemented by the Mysten Labs team. 

## Security Considerations

TODO: Discuss what measures you have taken to secure the certificate signing key. Discuss whether applications can create client ID against your issuer. 

TODO: Discuss worst case scenarios. If the JWK endpoint is unavailable, all zkLogin wallets associated with the provider will be locked out of their wallet since JWT cannot be generated. If the signing key is compromised, all wallets associated with this provider will result in loss of funds since anyone can forfeit the JWT and ZK proof as a result. 


## Copyright

```
REMOVE THIS BLOCK

This section is optional but recommended.
```
