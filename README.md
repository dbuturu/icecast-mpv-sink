# icecast-mpv-sink
---

`icecast-mpv-sink` is a lightweight service designed to continuously stream audio from an Icecast server to local audio output using MPV. It runs as a `systemd` service, ensuring automatic restart on interruptions and enabling seamless background operation.

## Features

- **Continuous Streaming**: Streams audio from Icecast sources directly to your local machine.
- **Enhanced Error Handling**: Automatically handles network interruptions, minimizing disruptions in streaming.
- **Broader MPV Configuration Options**: Flexible configuration through `/etc/icecast-mpv-sink/icecast-mpv-sink.conf`, allowing customization of MPV playback settings.
- **Systemd Integration**: Runs as a `systemd` service, with automatic restart and resilience to interruptions.
- **Configurable Setup**: Customize settings via the configuration file in `/etc/icecast-mpv-sink/icecast-mpv-sink.conf`.
- **Easy Installation**: Available as a `.deb` package, simplifying installation and setup.

## Installation

1. **Download the Latest Release**:
   - Go to the [Releases page](https://github.com/dbuturu/icecast-mpv-sink/releases) and download the latest `.deb` package.

2. **Install the Package**:
   ```bash
   sudo apt install ./icecast-mpv-sink_<version>.deb
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

- `stream.url`: URL of the Icecast stream.
- `[mpv]` options: Additional MPV settings, such as volume and video options.

Example configuration:
```ini
[stream]
ICECAST_IP=your-icecast-server-url
ICECAST_URL=http://your-icecast-server-url:8000/stream

[mpv]
no_video=true
volume=75
```

These settings allow you to customize playback parameters without modifying the service file.

## Usage

After installation, the service will automatically start and connect to the Icecast server specified in the configuration file. You can check its status or control the service with `systemctl`:

```bash
# Check status
sudo systemctl status icecast-mpv-sink.service

# Restart the service
sudo systemctl restart icecast-mpv-sink.service
```

## Error Handling and Troubleshooting

The service includes enhanced error handling:

- **Network Interruptions**: Automatically waits for network availability before starting playback, reducing errors due to network drops.
- **Automatic Restart**: The service will automatically restart on MPV failure or network disconnection.

**Common Commands:**
- **Check Service Status**: Run `sudo systemctl status icecast-mpv-sink.service` to see logs.
- **Network Check**: Ensure the Icecast server address is reachable.
- **Configuration Updates**: After updating `/etc/icecast-mpv-sink/icecast-mpv-sink.conf`, restart the service:
  ```bash
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
