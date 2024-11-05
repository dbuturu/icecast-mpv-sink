# icecast-mpv-sink
---

`icecast-mpv-sink` is a lightweight service designed to continuously stream audio from an Icecast server to local audio output using MPV. It runs as a `systemd` service, ensuring automatic restart on interruptions and enabling seamless background operation.

## Features

- **Continuous Streaming**: Streams audio from Icecast sources directly to your local machine.
- **Systemd Integration**: Runs as a systemd service, with automatic restart and resilience to interruptions.
- **Configurable Setup**: Customize settings via the configuration file in `/etc/icecast-mpv-sink/icecast-mpv-sink.conf`.
- **Easy Installation**: Available as a `.deb` package, simplifying installation and setup.

## Installation

1. **Download the Latest Release**:
   - Go to the [Releases page](https://github.com/dbuturu/icecast-mpv-sink/releases) and download the latest `.deb` package.

2. **Install the Package**:
   ```bash
   sudo dpkg -i icecast-mpv-sink_<version>.deb
   ```

3. **Adjust Configuration (Optional)**:
   - Modify `/etc/icecast-mpv-sink/icecast-mpv-sink.conf` to set your Icecast server URL and other preferences.

4. **Enable and Start the Service**:
   ```bash
   sudo systemctl enable icecast-mpv-sink.service
   sudo systemctl start icecast-mpv-sink.service
   ```

## Configuration

The configuration file is located at `/etc/icecast-mpv-sink/icecast-mpv-sink.conf`. Here, you can specify:
- `ICECAST_URL`: URL of the Icecast stream.
- `MPV_OPTIONS`: Optional parameters for MPV to modify playback settings.

Example configuration:
```ini
ICECAST_URL=http://your-icecast-server-url:8000/stream
MPV_OPTIONS=--no-video --volume=75
```

## Usage

After installation, the service will automatically start and connect to the Icecast server specified in the configuration file. You can check its status or control the service with `systemctl`:

```bash
# Check status
sudo systemctl status icecast-mpv-sink.service

# Restart the service
sudo systemctl restart icecast-mpv-sink.service
```

## Development

To build the `.deb` package locally:
1. Clone the repository and navigate into the directory.
2. Run the following command:
   ```bash
   dpkg-deb --build icecast-mpv-sink
   ```

## Contributing

Contributions are welcome! Please open an issue to discuss any changes or improvements.

## License

This project is licensed under the MIT License.
