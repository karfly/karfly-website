# karfly.github.io

## How to deploy as TON Site
1. Run Caddy redirect server:
```bash
docker compose up --build -d
```

2. Download TON reverse-proxy:
```bash
wget -O tonutils-reverse-proxy https://github.com/ton-utils/reverse-proxy/releases/latest/download/tonutils-reverse-proxy-linux-arm64
chmod +x tonutils-reverse-proxy
```

3. First run of reverse proxy (to get config and approve transaction with QR-code):
```bash
./tonutils-reverse-proxy --domain karfly.ton
```

4. Edit config:
```bash
sudo vim config.json  # set "proxy_pass": "http://127.0.0.1:12169/"
```

5. Run TON reverse-proxy (in daemon mode):
```bash
./tonutils-reverse-proxy --domain karfly.ton &
```

6. Stop TON reverse-proxy:
```bash
ps aux | grep tonutils-reverse-proxy
kill -9 XXX
```