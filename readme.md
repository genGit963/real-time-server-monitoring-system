# Real-Time Server Monitoring System

A simple, real-time monitoring service built with Go (Golang), designed to be a lightweight alternative to traditional systems like Nagios. This system provides live monitoring for servers, using WebSockets for real-time data updates.

## Features

- Real-time server monitoring via WebSocket connections
- Compatible with PostgreSQL (other databases can be integrated as needed)
- Integrates with Pusher or Pusher alternatives like [ipê](https://github.com/dimiro1/ipe)
- Configurable for various platforms (Linux, macOS, Windows)

---

## Prerequisites

- **PostgreSQL** version 11 or later
- A Pusher account (or a compatible alternative like [ipê](https://github.com/dimiro1/ipe))

## Getting Started

### Clone the Repository

```sh
git clone https://github.com/your-repo/real-time-monitoring-system.git
cd real-time-monitoring-system
```

### Build

#### For macOS/Linux

```sh
go build -o vigilate cmd/web/*.go
```

#### For Windows

```sh
go build -o vigilate.exe cmd/web/.
```

#### Cross-Platform (Example: Linux/AMD64)

```sh
env GOOS=linux GOARCH=amd64 go build -o vigilate cmd/web/*.go
```

## Running the Application

1. **Set Up ipê (if using as a Pusher alternative)**

   - **macOS/Linux**:

     ```sh
     cd ipe
     ./ipe
     ```

   - **Windows**:
     ```sh
     cd ipe
     ipe.exe
     ```

2. **Start the Monitoring System**

   Run the application with the required flags:

   ```sh
   ./vigilate \
   -dbuser='tcs' \
   -pusherHost='localhost' \
   -pusherPort='4001' \
   -pusherKey='123abc' \
   -pusherSecret='abc123' \
   -pusherApp="1" \
   -pusherSecure=false
   ```

## Configuration Flags

Here are the available flags for configuring the application:

| Flag            | Description                      | Default     |
| --------------- | -------------------------------- | ----------- |
| `-db`           | Database name                    | `vigilate`  |
| `-dbhost`       | Database host                    | `localhost` |
| `-dbport`       | Database port                    | `5432`      |
| `-dbssl`        | Database SSL setting             | `disable`   |
| `-dbuser`       | Database user                    |             |
| `-domain`       | Domain name (e.g., example.com)  | `localhost` |
| `-identifier`   | Unique identifier                | `vigilate`  |
| `-port`         | Application port                 | `:4000`     |
| `-production`   | Set for production               | `false`     |
| `-pusherApp`    | Pusher app ID                    | `9`         |
| `-pusherHost`   | Pusher host                      |             |
| `-pusherKey`    | Pusher key                       |             |
| `-pusherPort`   | Pusher port                      | `443`       |
| `-pusherSecret` | Pusher secret                    |             |
| `-pusherSecure` | Use SSL with Pusher (true/false) | `false`     |

For help on flags, run:

```sh
./vigilate -help
```

---

## License

This project is open-source and licensed under the [MIT License](LICENSE).
