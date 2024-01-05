# Podman Compose Setup For Installing Passbolt

## Prerequisite

- Podman
- Internet connection
- A domain name
- Cert and Key
- Coffee

## ENV file examples

### .env.db

```ini
MYSQL_ROOT_PASSWORD=<root pw>
MYSQL_DATABASE=<db>
MYSQL_USER=<user>
MYSQL_PASSWORD=<user pw>
```

### .env.passbolt

```ini
APP_FULL_BASE_URL=https://<domain>
DATASOURCES_DEFAULT_HOST=db
DATASOURCES_DEFAULT_USERNAME=<user>
DATASOURCES_DEFAULT_PASSWORD=<user pw>
DATASOURCES_DEFAULT_DATABASE=<db>
PASSBOLT_META_TITLE=Toms IT Cafe
PASSBOLT_META_DESCRIPTION=Coffee and IT for a better life
```

### .env.passbolt_smtp

Passbolt relies on email sending so setting up the SMTP service is a must.

```ini
EMAIL_DEFAULT_FROM_NAME=Passbolt
EMAIL_DEFAULT_FROM=tmolnar0831@gmail.com
EMAIL_TRANSPORT_DEFAULT_HOST=<smtp host>
EMAIL_TRANSPORT_DEFAULT_PORT=<smtp port>
EMAIL_TRANSPORT_DEFAULT_USERNAME=tmolnar0831@gmail.com
EMAIL_TRANSPORT_DEFAULT_PASSWORD=<app code>
EMAIL_TRANSPORT_DEFAULT_TLS=true
```

## Usage

```bash
podman-compose up -d
```

## Author

Tamas Molnar - <tmolnar0831@gmail.com> - [https://tomsitcafe.com](https://tomsitcafe.com)
