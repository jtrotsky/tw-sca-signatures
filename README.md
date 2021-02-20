## Getting statements from TransferWise API with SCA

API users in the UK / Europe / EEA need to satisfy a Strong Customer Authentication (SCA) challenge from TransferWise when they are moving money or reading account statements. This is an additional security check to comply with the 2nd Payment Services Directive (PSD2) regulation. 

How it works is that a standard API call to pull an account statement will fail with HTTP 403 and an 'x-2fa-approval' header with a one-time-token value. The user will need to sign the one-time-token with a private key that corresponds to a public key uploaded to their TransferWise account. They can then retry the same request including the signed header and the request can succeed.

This repo contains code examples of this in Python and Go. 

- Python: [get-statements-sca.py](https://github.com/jtrotsky/tw-statements-sca/blob/main/get-statements-sca.py)
- Go: [get-statements-sca.go](https://github.com/jtrotsky/tw-statements-sca/blob/main/get-statements-sca.go)

## API Documentation
- [TW API: Get Account Statements](https://api-docs.transferwise.com/#borderless-accounts-get-account-statement)
- [TW API: Strong Customer Authentication](https://api-docs.transferwise.com/#strong-customer-authentication)
