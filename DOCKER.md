# Docker 部署

## 启动

```bash
docker compose up -d --build
```

访问：

```text
http://服务器IP:8000
```

本机访问：

```text
http://127.0.0.1:8000
```

## 查看日志

```bash
docker compose logs -f
```

## 停止

```bash
docker compose down
```

## 持久化文件

`docker-compose.yml` 会把本地 `./data` 目录挂载到容器的 `/app/data`。

容器内会持久化这些文件：

- `/app/data/config.json`：系统设置
- `/app/data/tasks.json`：任务记录
- `/app/data/screenshots/`：导出的 Cookie 结果

如果在面板里部署，只挂载一条硬盘：

```text
硬盘 ID: adobe-data
挂载目录: /app/data
```

并添加环境变量：

```text
DATA_DIR=/app/data
```

## 代理说明

代理检测和注册流量都从容器发起。部署到服务器后，如果代理商开启 IP 白名单，需要把服务器公网 IP 加到代理白名单。
