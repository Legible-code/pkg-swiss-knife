# pkg-swiss-knife

Minimal & operational Bash script that updates multiple package managers and cleans up unused packages.

**Current support:**  
- **APT** (via [`nala`](https://github.com/volitank/nala) — a faster, prettier and more readable front-end)  
- **Flatpak**

## Why?

I got tired of manually typing in basic maintaince commands and other scripts were bloated(for my use case).
one executable and you are done. 

## Requirements

- Bash (99% chance you already have it - ubuntu/fedora/debian/linux-mint etc come with bash preinstalled)
- `sudo` privileges 
- [`nala`](https://github.com/volitank/nala) installed (used instead of `apt` directly)

## Installation

1. Clone or download the script:
   ```bash
   git clone https://github.com/your-username/pkg-swiss-knife.git
   cd pkg-swiss-knife
   ```
2. Make it executable:
   ```bash
   chmod +x pkg-swiss-knife.sh
   ```
3. (Optional) Move it to your PATH:
   ```bash
   sudo cp pkg-swiss-knife.sh /usr/local/bin/pkg-swiss-knife
   ```

## Usage

Run with:
```bash
./pkg-swiss-knife.sh
```
Or, if installed to PATH:
```bash
pkg-swiss-knife
```

The script will:
- Update APT packages using `nala`
- Remove unused APT packages
- Update Flatpak runtimes/apps
- Remove unused Flatpak packages

## What it does (under the hood)

- **APT (via nala)**
  - `nala upgrade --assume-yes`
  - `nala autopurge` / `nala autoremove`
- **Flatpak**
  - `flatpak update --assumeyes`
  - `flatpak uninstall --unused`

This mirrors common manual maintenance steps but runs them in one place.

## Roadmap / TODO

- **Asynchronous execution**  
  Run package manager operations in parallel to reduce total runtime, especially as more managers are added. This will include a structured debug/log system for traceability.
- **Nix support**  
  Add detection and update/cleanup flows for Nix packages.
- **Homebrew support**  
  Add detection and update/cleanup flows for Homebrew (Linux/macOS).

Contributions and suggestions are welcome—especially around safe parallelization and logging.

## Notes

- The script requires `sudo` for APT/nala operations. Flatpak may also require elevation depending on your installation (system vs user).
- If you prefer `apt` over `nala`, you can adapt the APT section easily; the script is intentionally simple to customize.
