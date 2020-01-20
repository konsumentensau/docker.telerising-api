# docker.telerising-api
A docker container for running telerising API

### Prerequisites
You will need to have `docker` installed on your system and the user you want to run it needs to be in the `docker` group.

> **Note:** The image is a multi-arch build providing variants for amd64, arm32v7 and arm64v8 - the correct variant for your Architecture needs to be tagged eg :amd64 :arm32v7 :arm64v8

## Technical info for Docker
To learn how to manually start the container or about available parameters (you might need for your GUI used) see the following example:

```
docker run \
  -d \
  -e USER_ID="99" \
  -e GROUP_ID="100" \
  -e TIMEZONE="Europe/Berlin" \
  -e UPDATE="yes" \
  -e PROVIDER="zattoo.com" \
  -e LOGIN="firstname.lastname@example.com" \
  -e PASSWORD="mypassword123" \
  -e SERVER="fr5-0" \
  -v {TELERISING_STORAGE}:/telerising \
  --name=telerising-api \
  --restart unless-stopped \
  --tmpfs /tmp \
  --tmpfs /var/log \
  takealug/telerising-api:tag
```

The available parameters in detail:

| Parameter | Optional | Values/Type | Default | Description |
| ---- | --- | --- | --- | --- |
| `USER_ID` | yes | [integer] | 99 | UID to run easyepg as |
| `GROUP_ID` | yes | [integer] | 100 | GID to run easyepg as |
| `TIMEZONE` | yes | [string] | Europe/Berlin | Timezone for the container |
| `PROVIDER` | no | [string] | zattoo.com | The Provider / Reseller u USE |
| `LOGIN` | no | [string] | firstname.lastname@example.com | Your Provider Account NAME |
| `PASSWORD` | no | [string] | mypassword123 | Your Account Password |
| `SERVER` | yes | [string] | fr5-0 | The Server u want to use |

Frequently used volumes:
 
| Volume | Optional | Description |
| ---- | --- | --- |
| `TELERISING_STORAGE` | no | The directory to persist easyepg to |


When passing volumes please replace the name including the surrounding curly brackets with existing absolute paths with correct permissions.


