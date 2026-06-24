# gql-2fa-bypass

Bypasses GraphQL 2FA OTP rate limiting using query batching.

## Usage

pip install requests
python3 gql_2fa_bypass.py

## Configuration

Update these variables at the top of the script:

HOST = "http://<TARGET_IP>:<PORT>"
EMAIL = "admin@example.com"
PASSWORD = "password123"

## How it works

1. Logs in as the target user to trigger 2FA
2. Extracts the 2FA session token from the error response
3. Sends OTP guesses in batches of 100 per request to bypass rate limiting
4. Prints the valid OTP and auth token when found

## Technique

GraphQL allows multiple mutations in a single request (batching). Servers that rate limit individual requests often fail to apply the same limits to batched queries, allowing brute force attacks that would otherwise be blocked.

## Example Output

[*] 2FA token: a1f0b20e-99cf-4536-8447-44c07c74e028
[*] Tried 100/10000...
[*] Tried 200/10000...
[+] Valid OTP: 1130
[+] Auth token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...

## Disclaimer

For educational purposes and authorized penetration testing only.
