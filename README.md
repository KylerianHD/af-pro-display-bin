# af-pro-display-bin

AUR package for [af-pro-display](https://github.com/nishtahir/antec-flux-pro-display) by [nishtahir](https://github.com/nishtahir), a systemd service that shows CPU and GPU temperatures on the [Antec Flux Pro](https://www.antec.com/product/case/flux-pro) case display under Linux.

## Installation

**Using an AUR helper:**
```bash
yay -S af-pro-display-bin
# or
paru -S af-pro-display-bin
```

**Manually:**
```bash
git clone https://aur.archlinux.org/af-pro-display-bin.git
cd af-pro-display-bin
makepkg -si
```

Then enable the service:
```bash
sudo systemctl enable --now af-pro-display
```

## USB access

USB access is handled automatically via the bundled udev rule using the `uaccess` tag. After installing, reconnect the display or reload udev rules if the device was already plugged in:

```bash
sudo udevadm control --reload-rules && sudo udevadm trigger
```

## Configuration

The service reads `~/.config/af-pro-display/config.toml`. Example:

```toml
cpu_device = "/sys/class/hwmon/hwmon0/temp1_input"
polling_interval = 200
```

## Service management

```bash
sudo systemctl status af-pro-display
sudo systemctl stop af-pro-display
sudo systemctl start af-pro-display
sudo systemctl disable af-pro-display
sudo systemctl enable af-pro-display
```

## Credits

- [nishtahir/antec-flux-pro-display](https://github.com/nishtahir/antec-flux-pro-display) - upstream project

## License

The packaging files in this repository are licensed under [GPL-3.0](LICENSE).
The packaged software itself is licensed under [GPL-3.0](https://github.com/nishtahir/antec-flux-pro-display/blob/main/LICENSE).

