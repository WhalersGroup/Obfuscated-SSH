# Obfuscated-SSH
Obfuscated SSH Configuration Linux-Servers/Linux-Clients/Android-Clients/Windows-Clients

## Server
### Debian 12
```bash
wget https://deb.zinglau.com/pubkey.pgp -O /etc/apt/keyrings/deb_zinglau_com.pgp
cat <<EOF > /etc/apt/sources.list.d/obfuscated_openssh.sources
# OpenSSH with obfuscated handshake
Types: deb deb-src
URIs: https://deb.zinglau.com/debian
Suites: bookworm
Components: main
Signed-By: /etc/apt/keyrings/deb_zinglau_com.pgp
EOF
```

### Debian <= 11
```bash
wget https://deb.zinglau.com/pubkey.pgp -O - | apt-key add -
echo "deb https://deb.zinglau.com/debian/ bullseye main" > /etc/apt/sources.list.d/obfuscated_openssh.list
```

### Debian
Configure Preferences: create a file in `` /etc/apt/preferences.d/ ``
```bash

Package: *
Pin: release o=zinglau.com
Pin-Priority: 600

```

### Ubuntu
```bash

sudo add-apt-repository ppa:zinglau/obfuscated-openssh
sudo apt update

```
<br/>

Configure Preferences: Create a file in ``/etc/apt/preferences.d/``
```bash

Package: *
Pin: release o=zinglau.com
Pin-Priority: 600

```

### sshd_config

```bash

Port 22
ObfuscatedPort 222
ObfuscateKeyword key

```

```bash
/usr/local/bin/ssh -z -Z yourkey -p 222 -v localhost
```
