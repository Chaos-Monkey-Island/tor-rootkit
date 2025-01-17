# tor-rootkit
[![Docker build test](https://github.com/emcruise/TorRootkit/actions/workflows/docker-test.yml/badge.svg)](https://github.com/emcruise/TorRootkit/actions/workflows/docker-test.yml)
[![Windows & Linux executables](https://github.com/emcruise/tor-rootkit/actions/workflows/release.yml/badge.svg)](https://github.com/emcruise/tor-rootkit/actions/workflows/release.yml)

A Python 3 standalone Windows 10 / Linux Rootkit. The networking communication get's established over the tor network.

## Disclaimer
Use for educational purposes only.

## How to use

1. Clone the repo and change directory:
```bash
git clone https://github.com/emcruise/tor-rootkit.git
cd ./tor-rootkit
```

2. Build docker container:
```bash
docker build -t listener .
```

3. Run docker container:
```bash
docker run -v $(pwd)/executables:/executables/ -it listener
```

4. Deploy the executables:
When the listener is up and running it generates a "executables" directory containing different payloads for different plattforms.
```
tor-rootkit/
│    ...
└    executables/
```

**Note: The client can take some time to connect because PyInstaller executables are a bit slower and it need's to start tor.**

## Features
- Standalone executables for Windows and Linux, including python interpreter and tor
- the whole communication works over tor hidden services which guarantees some degree of anonymity
- The Listener can handle multiple clients
- The Listener generates payloads for different platforms on startup

## Listener Shell Commands
| Command | Explanation |
| ------- | ----------- |
| `help`  | Shows the help menu |
| `^C` or `exit` | Exits the shell |
| `list` | lists all connected clients with their according index |
| `select <index>` | start shell with client |

## Client Shell Commands
| Command | Explanation |
| ------- | ----------- |
| `help`  | Shows the help menu |
| `^C` or `exit` | Exits the client shell and returns to listener shell |
| `os <command>` | Executes a command in the clients shell and returns the output |
| `background` | Keeps the connection to a client and returns to listener

## Contribution

Any contributions are appreciated. Make a pull-requests and I'll merge if it passes my automatic tests.
