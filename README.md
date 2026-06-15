## ⭐ Stellar Node

`starknode-kit` includes a dedicated CLI runner for [Stellar Core](https://developers.stellar.org/docs/validators/admin-guide/running-node) (`stellar-core`) validator nodes. All Stellar commands live under the `stellar` sub-command.

### Stellar Sub-commands

| Sub-command                     | Description                                                  |
| ------------------------------- | ------------------------------------------------------------ |
| `stellar install`               | Install stellar-core via apt (Ubuntu/Debian) or Homebrew (macOS) |
| `stellar init-db`               | Initialise the stellar-core database (run once before first start) |
| `stellar start`                 | Start stellar-core in the background                         |
| `stellar status`                | Show live node status via the `info` HTTP command            |
| `stellar http-command <cmd>`    | Send any admin HTTP command to the running node              |
| `stellar version`               | Print the installed stellar-core version                     |
| `stellar remove`                | Remove the managed stellar-core installation                 |

### Stellar Flags

| Flag          | Default    | Description                                      |
| ------------- | ---------- | ------------------------------------------------ |
| `--network`   | `pubnet`   | Network to join: `pubnet` (mainnet) or `testnet` |
| `--conf`      | managed    | Path to a custom `stellar-core.cfg`              |
| `--http-port` | `11626`    | stellar-core local HTTP admin port               |

### Stellar Quick Start

**1. Install stellar-core**

```bash
starknode-kit stellar install
```

**2. Place your `stellar-core.cfg`**

Put a valid configuration file at the managed path (printed during install), or pass `--conf /path/to/your/stellar-core.cfg` to each command.

Reference: [https://developers.stellar.org/docs/validators/admin-guide/configuring](https://developers.stellar.org/docs/validators/admin-guide/configuring)

**3. Initialise the database**

```bash
starknode-kit stellar init-db
```

**4. Start the node**

```bash
# Mainnet (pubnet)
starknode-kit stellar start --network pubnet

# Testnet
starknode-kit stellar start --network testnet
```

**5. Check node status**

```bash
starknode-kit stellar status
```

**6. Send admin HTTP commands**

```bash
# Node info
starknode-kit stellar http-command info

# Connected peers
starknode-kit stellar http-command peers

# Quorum health
starknode-kit stellar http-command quorum

# SCP state
starknode-kit stellar http-command scp
```

### Stellar Data Directories

All managed Stellar data lives under:

```
~/.config/starknode-kit/stellar_clients/stellar-core/
├── stellar-core        ← symlink to the installed binary
├── stellar-core.cfg    ← default config location
├── logs/               ← timestamped log files
└── database/           ← ledger database
```

---

## 📋 Requirements

### 🛠️ Software Dependencies

Make sure the following are installed on your system before using or building `starknode-kit`:

- **Go**: Version **1.24 or later**
  Install from: [https://go.dev/dl/](https://go.dev/dl/)

- **Rust**: Recommended for building Starknet clients (e.g., Juno)
  Install with:

  ```bash
  curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
  ```

- **Make**: Required to build certain clients and scripts
  Install via package manager:

  - Ubuntu/Debian: `sudo apt install make`
  - macOS (with Homebrew): `brew install make`
  - Windows (WSL): included or `sudo apt install make`

### 🖥️ Hardware Requirements

See this [Rocket Pool Hardware Guide](https://docs.rocketpool.net/guides/node/hardware.html) for a detailed breakdown of node hardware requirements.

- **CPU**: Node operation doesn't require heavy CPU power. The BG Client has run well on both i3 and i5 models of the ASUS NUC 13 PRO. Be cautious if using Celeron processors, as they may have limitations.
- **RAM**: At least **32 GB** is recommended for good performance with overhead.
- **Storage (SSD)**: The most critical component. Use a **2 TB+ NVMe SSD** with:

  - A **DRAM cache**
  - **No Quad-Level Cell (QLC)** NAND architecture
    See this [SSD List Gist](https://gist.github.com/bkase/fab02c5b3c404e9ef8e5c2071ac1558c) for tested options.

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 🌐 Join the Community

Join the community to stay updated, ask questions, or contribute:

- Telegram: [https://t.g/+-SCPbza9fk8dkYWI0](https://t.me/+SCPbza9fk8dkYWI0)

Whether you're a seasoned validator, hobbyist, or first-time node runner, you're welcome!

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
