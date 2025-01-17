# RECAR
Reversed engineered server for RACER: The Chrome Experiment

# DISCLAIMER
Re-hosting the official client may be against Google's license. We are not responsible for any damages caused.

## Getting Started

### Server
The server runs on HTTPS + WSS, so you need to create an SSL certificate and key using the following commands:

```sh
mkdir ssl
cd ssl
openssl req -nodes -new -x509 -keyout server.key -out server.cert
```

Rename `config.example.json` to `config.json` and edit as necessary.

Start the server by running:
```sh
npm install
npm start
```

### Client
As we need the official client which can be assumed non-redistributable, we use a downloader script to download (and prettify) the client straight from Google's servers:

```sh
# For prettification of minified source
sudo npm install -g prettier
./download_client.sh
```

This will create a `client` folder in your repo. Open `client/assets/js/racer.js` and replace lines containing `<server_ip>:<server_port>` with the corresponding values from `config.json`. Save and connect to the client via `https://<server_ip>:<server_port>/racer/`