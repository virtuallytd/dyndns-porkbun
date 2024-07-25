
# Porkbun Dynamic DNS Updater

This project provides a Go-based solution for dynamically updating DNS records with Porkbun's API. It periodically checks your public IP address and updates the DNS record if the IP address has changed.

## Prerequisites

- Docker
- Go 1.16 or later (if running without Docker)

## Setup

### Docker

1. **Create the `.env` file**:

   ```plaintext
   PORKBUN_API_KEY=your_porkbun_api_key
   PORKBUN_SECRET_KEY=your_porkbun_secret_key
   DOMAIN=example.com
   SUBDOMAIN=www
   RECORD_TYPE=A
   UPDATE_INTERVAL=300
   ```

2. **Build the Docker image**:

   ```sh
   docker build -t porkbun-dynamic-dns .
   ```

3. **Run the Docker container**:

   ```sh
   docker run --env-file .env porkbun-dynamic-dns
   ```

### Without Docker

1. **Install dependencies**:

   ```sh
   go mod download
   ```

2. **Create the `.env` file**:

   ```plaintext
   PORKBUN_API_KEY=your_porkbun_api_key
   PORKBUN_SECRET_KEY=your_porkbun_secret_key
   DOMAIN=example.com
   SUBDOMAIN=www
   RECORD_TYPE=A
   UPDATE_INTERVAL=300
   ```

3. **Run the application**:

   ```sh
   go run main.go
   ```

## Configuration

- `PORKBUN_API_KEY`: Your Porkbun API key.
- `PORKBUN_SECRET_KEY`: Your Porkbun secret API key.
- `DOMAIN`: The domain name you want to update.
- `SUBDOMAIN`: The subdomain you want to update.
- `RECORD_TYPE`: The type of DNS record to update (default is `A`).
- `UPDATE_INTERVAL`: The interval in seconds between checks for the public IP address (default is `300`).

## Example

Here is an example `.env` file:

```plaintext
PORKBUN_API_KEY=abc123
PORKBUN_SECRET_KEY=xyz456
DOMAIN=example.com
SUBDOMAIN=www
RECORD_TYPE=A
UPDATE_INTERVAL=300
```

## Logging

The application logs the following information:
- Errors encountered while getting the public IP or updating DNS records.
- Confirmation messages when DNS records are successfully created or updated.
- Messages indicating no update is needed if the IP address hasn't changed.

## License

This project is licensed under the MIT License.
