# Shadowsocks

## Configuration

Fill `inventory.ini` with server configuration:

```ini
[servers]
<your-domain-name> working_directory=<client-config-directory>
```

An absolute path specified in place of `<client-config-directory>` will contain client configuration file `client-config.json` after successful deployment.

Set connection password in `secrets.yml`:

```yaml
shadowsocks_config:
  password: '<your-password>'
```

## Deploy

```sh
$ ansible-playbook deploy.yml
```

The script will install acme.sh

## Usage

### Android

You need to install [Shadowsocks client](https://github.com/shadowsocks/shadowsocks-android/releases) and [xray-plugin](https://github.com/teddysun/xray-plugin-android/releases).

## Cleanup

You can remove most of the side-effects of the script by running

```sh
$ ansible-playbook cleanup.yml
```
