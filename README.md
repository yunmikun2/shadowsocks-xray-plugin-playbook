# Shadowsocks

## Configuration

Fill `inventory.ini` with server configuration:

```ini
[servers]
<your-domain-name>
```

It must be a real domain name, and your SSH needs to be configured so that you can connect to the server by simply typing `ssh <your-domain-name>`.

Set connection password in `secrets.yml`:

```yaml
shadowsocks_config:
  password: '<your-password>'
```

## Deploy

```sh
$ ansible-playbook deploy.yml
```

The script does the following.
1. Installs acme.sh, issues a TLS certificate for your domain and sets up its renewal.
2. Sets up and configures shadowsocks with the plugin.
3. Starts shadowsocks with the configuration provided.
4. Blocks all the connections to the server except from 22, 80, and 443 ports.

You will see "Connect URI" somewhere in the output. You also can regenerate it by running

```sh
$ ansible-playbook deploy.yml --tags client-config
```

## Usage

### Android

You need to install [Shadowsocks client](https://github.com/shadowsocks/shadowsocks-android/releases) and [xray-plugin](https://github.com/teddysun/xray-plugin-android/releases).

## Cleanup

You can remove most of the side-effects of the script by running

```sh
$ ansible-playbook cleanup.yml
```
