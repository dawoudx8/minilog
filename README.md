# minilog

`minilog` is a minimal, color-coded, human-readable logging library for Go, built for simplicity and clarity.

It supports multiple log levels, easy formatted logging, and structured context output — without adding complex configuration or dependencies beyond ANSI colors.

---

## Features

- Four log levels: `SUCCESS`, `ERROR`, `INFO`, `DEBUG`
- Colored output per level
- Easy formatting with `Successf`, `Errorf`, etc.
- Optional structured logging with context
- Timestamped output
- Simple toggle for debug mode

---

## Installation

```bash
go get github.com/dawoudx8/minilog
```

---

## Usage

### Basic
```go
package main

import "github.com/dawoudx8/minilog"

func main() {
    log := minilog.New(true) // enableDebug = true

    log.Success("Server started")
    log.Info("Listening on port 8080")
    log.Error("Failed to connect to database")
    log.Debug("User ID = 12345")
}
```

### Formatted
```go
log.Infof("User %s logged in", username)
log.Errorf("Failed to load file: %v", err)
```

### Context Logging
```go
log.LogWithContext(minilog.ERROR, "Auth", "Login", "session-123", "Invalid password")
log.LogWithContext(minilog.INFO, "HTTP", "GET /users", "session-xyz", "")
```

---

## Output Example
```text
[12:31:01.123] [+] [SUCCESS] Server started
[12:31:01.456] [!] [INFO] Listening on port 8080
[12:31:01.789] [-] [ERROR] Failed to connect to database
[12:31:02.000] [~] [DEBUG] User ID = 12345
```

---

## API Reference

### Logger Methods
| Method | Description |
|--------|-------------|
| `Success(msg)` | Print success message |
| `Error(msg)`   | Print error message   |
| `Info(msg)`    | Print info message    |
| `Debug(msg)`   | Print debug message (only if enabled) |
| `Successf(format, ...)` | Formatted version of `Success` |
| `Errorf(format, ...)`   | Formatted version of `Error`   |
| `Infof(format, ...)`    | Formatted version of `Info`    |
| `Debugf(format, ...)`   | Formatted version of `Debug`   |
| `LogWithContext(level, component, action, sessionID, extra)` | Log structured message with metadata |

---

## License

MIT

---

## Credits

Built using [fatih/color](https://github.com/fatih/color) for terminal color support.

---

## Author

Maintained by [your name] — feel free to fork or contribute!

