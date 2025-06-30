#scripts for server services

```bash
sudo vi /etc/systemd/system/yuze-code-tunnel.timer
```

```bash
sudo vi /etc/systemd/system/yuze-code-tunnel.service
```

```bash
sudo systemctl daemon-reload
```

```bash
sudo systemctl start yuze-code-tunnel.service
```

```bash
sudo systemctl start yuze-code-tunnel.timer
```