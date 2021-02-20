## Getting statements from TransferWise API with SCA

API users in the UK / Europe / EEA need to satisfy a Strong Customer Authentication (SCA) challenge from TransferWise when they are moving money or reading account statements. This is an additional security check to comply with the 2nd Payment Services Directive (PSD2) regulation. 

How it works is that a standard API call to pull an account statement will fail with HTTP 403 and an 'x-2fa-approval' header with a one-time-token value. The user will need to sign the one-time-token with a private key that corresponds to a public key uploaded to their TransferWise account. They can then retry the same request including the signed header and the request can succeed.

This repo contains code examples of this in Python and Go. 

- Python: [get-statements-sca.py](https://github.com/jtrotsky/tw-sca-signatures/blob/main/get-statements-sca.py)
- Go: [get-statements-sca.go](https://github.com/jtrotsky/tw-sca-signatures/blob/main/get-statements-sca.go)
- Java: example in an external pkg, see below.

### Usage
1. Read the TransferWise documentation, generate your keypair and upload your public key.
2. Add your profile ID, borderless account ID, and private key file path to the script.
3. Add your API token as an env var with key: API_TOKEN
```
$ export API_TOKEN=<YOUR API TOKEN HERE>
```
4. Run the script 
```
$ go run get-statements-sca.go
OR
$ python3 get-statements-sca.py
```

### API Documentation
- [TW API: Get Account Statements](https://api-docs.transferwise.com/#borderless-accounts-get-account-statement)
- [TW API: Strong Customer Authentication](https://api-docs.transferwise.com/#strong-customer-authentication)

### Other resources
- [Java Implementation](https://github.com/transferwise/digital-signatures)
