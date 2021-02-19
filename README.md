# ib-tws-docker

This builds a Docker image with the latest version of [Interactive Brokers](https://interactivebrokers.com)' [Trader Workstation](https://www.interactivebrokers.com/en/index.php?f=5041), the modern [IbcAlpha/IBC](https://github.com/IbcAlpha/IBC) for automation, and a VNC server for debugging purposes.

## Building

```sh
docker build . -t ib-tws-docker --build-args VNC_PASSORD=XXXX
```

where `XXXX` is a password you'd like to use to login to the VNC server.

## Running

```sh
docker run -p 7497:7497 -p 5900:5900 \
    --env TWSUSERID=YOUR_USER_ID \
    --env TWSPASSWORD=YOUR_PASSWORD \
    ib-tws-docker:latest
```

This will expose port 7497 for the TWS API (usable with, e.g., [ib_insync](https://github.com/erdewit/ib_insync)) and 5900 for VNC (with default password `XXXX`). **Neither are secure for public internet access**, as the expectation is that private, secure services will sit on top and be the only open interface to the internet.
