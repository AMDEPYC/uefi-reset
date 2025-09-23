# UEFI Reset Modules

A set of simple UEFI modules that reset the system when loaded. Written in Rust
with minimal dependencies and no unsafe code. Building this project produces a
set of binaries:

* `shutdown.efi` - Powers off the system.
* `cold.efi` - Performs a cold reset.
* `warm.efi` - Performs a warm reset.

## Purpose

This application is designed to be loaded by UEFI firmware and will immediately 
trigger a system reset. This provides a quick and convenient way to power off
or reboot a system from:

- A bootable USB drive
- A UEFI shell
- UEFI HTTP boot
- Any EFI-capable firmware interface

## Building

### Prerequisites

- Rust 1.81+ toolchain

The project includes a `rust-toolchain.toml` file that automatically installs the
required `x86_64-unknown-uefi` target. However, depending on your environment you
might need to manually install the target.

### Steps

To build the project:
   
```bash
cargo build --release --target=x86_64-unknown-uefi
```

The above command will produce three files of note:

* `target/x86_64-unknown-uefi/release/cold.efi`
* `target/x86_64-unknown-uefi/release/warm.efi`
* `target/x86_64-unknown-uefi/release/shutdown.efi`

The `--target` option is likely optional for any tools that respect `.cargo/config.toml`.

## License

This project is licensed under the MIT License.
