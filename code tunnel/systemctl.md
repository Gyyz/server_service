# scripts for server services
# re-run the code tunnel every 24 hours
1. create timmer
```bash
sudo vi /etc/systemd/system/yuze-code-tunnel.timer
```


2. create service
```bash
sudo vi /etc/systemd/system/yuze-code-tunnel.service
```


3. re-load the services
```bash
sudo systemctl daemon-reload
```

4. start the service
```bash
sudo systemctl start yuze-code-tunnel.service
```


5. start the timmer
```bash
sudo systemctl start yuze-code-tunnel.timer
```