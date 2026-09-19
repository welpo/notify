# notify

a convenience wrapper around [ntfy](https://ntfy.sh). sends a notification, titled with the machine (`hostname -s`) it came from

```sh
notify "nightly dump finished"
notify -t backup "nightly dump finished"
notify -l warning -t disk "3% free on /mnt/12TB_B"
```

the title is the hostname. `-t` appends a label to it, so the second line above arrives as **host: backup**

## levels

the level picks the emoji. default is `info`

| level | emoji |
| --- | --- |
| `debug` | 🐛 |
| `info` | 💬 |
| `success` | ✅ |
| `warning` | ⚠️ |
| `error` | ❌ |
| `critical` | 🚨 |

## setup

put `notify` on your `PATH` and write `~/.config/notify/config`:

```sh
topic="https://ntfy.example.com/alerts"
token="tk_..."
```

keep it private: `chmod 600 ~/.config/notify/config`

var env `NOTIFY_CONFIG` points at another config file. `NOTIFY_TOPIC` and `NOTIFY_TOKEN` override its values. without a topic and a token, `notify` exits 1 and sends nothing
