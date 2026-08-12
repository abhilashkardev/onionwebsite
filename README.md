# Onion Website (Tor Hidden Service)

This repository contains a minimal static website that can be published as a Tor Onion service.

## Project structure

- `/site/index.html` - main page
- `/site/styles.css` - page styling

## Run locally

From the repository root:

```bash
python3 -m http.server 8080 --directory site
```

Then open `http://127.0.0.1:8080`.

## Publish on Tor Onion network

1. Install Tor on your server/machine.
2. Add the following to your `torrc`:

```conf
HiddenServiceDir /var/lib/tor/onionwebsite/
HiddenServicePort 80 127.0.0.1:8080
```

3. Start your local web server:

```bash
python3 -m http.server 8080 --directory /absolute/path/to/onionwebsite/site
```

4. Restart Tor.
5. Read your Onion address:

```bash
sudo cat /var/lib/tor/onionwebsite/hostname
```

Use that `.onion` hostname in Tor Browser to access the website.