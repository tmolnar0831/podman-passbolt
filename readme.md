# Podman Compose Setup For Installing Passbolt

This configuration creates database and SSL reverse proxy containers for Passbolt.

Detailed info: [Tom's IT Cafe article on https://tomsitcafe.com](https://tomsitcafe.com/2023/12/22/install-passbolt-self-hosted-with-podman/)

## Prerequisite

- Podman
- Internet connection
- A domain name
- Cert and Key
- Coffee

## ENV file examples

### .env.db

This is the DB container configuration.

```ini
MYSQL_ROOT_PASSWORD=<root pw>
MYSQL_DATABASE=<db>
MYSQL_USER=<user>
MYSQL_PASSWORD=<user pw>
```

### .env.passbolt

This is the Passbolt service base configuration.

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

Passbolt relies heavily on email sending. Setting up the SMTP service is mandatory.

```ini
EMAIL_DEFAULT_FROM_NAME=Passbolt
EMAIL_DEFAULT_FROM=tmolnar0831@gmail.com
EMAIL_TRANSPORT_DEFAULT_HOST=<smtp host>
EMAIL_TRANSPORT_DEFAULT_PORT=<smtp port>
EMAIL_TRANSPORT_DEFAULT_USERNAME=tmolnar0831@gmail.com
EMAIL_TRANSPORT_DEFAULT_PASSWORD=<app code>
EMAIL_TRANSPORT_DEFAULT_TLS=true
```

### .env.mailalerts

The email alerting can be configured from the environment variables if necessary.

```ini
PASSBOLT_EMAIL_SEND_COMMENT_ADD=0
PASSBOLT_EMAIL_SEND_PASSWORD_CREATE=0
PASSBOLT_EMAIL_SEND_PASSWORD_SHARE=0
PASSBOLT_EMAIL_SEND_PASSWORD_UPDATE=0
PASSBOLT_EMAIL_SEND_PASSWORD_DELETE=0
PASSBOLT_EMAIL_SEND_USER_CREATE=0
PASSBOLT_EMAIL_SEND_USER_RECOVER=0
PASSBOLT_EMAIL_SEND_GROUP_DELETE=0
PASSBOLT_EMAIL_SEND_GROUP_USER_ADD=0
PASSBOLT_EMAIL_SEND_GROUP_USER_DELETE=0
PASSBOLT_EMAIL_SEND_GROUP_USER_UPDATE=0
PASSBOLT_EMAIL_SEND_GROUP_MANAGER_UPDATE=0
PASSBOLT_EMAIL_SEND_FOLDER_CREATED=0
PASSBOLT_EMAIL_SEND_FOLDER_UPDATED=0
PASSBOLT_EMAIL_SEND_FOLDER_DELETED=0
PASSBOLT_EMAIL_SEND_FOLDER_SHARE_CREATED=0
PASSBOLT_EMAIL_SEND_FOLDER_SHARE_DROPPED=0
```

## Usage

Place the certificate and key file in the `certs` folder of the project directory.

Start the services:

```bash
podman-compose up -d
```

## Author

Tamas Molnar - <tmolnar0831@gmail.com> - [https://tomsitcafe.com](https://tomsitcafe.com)
