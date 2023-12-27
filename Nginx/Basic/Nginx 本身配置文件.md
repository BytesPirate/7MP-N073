# nginx.conf 文件配置

```nginx config
# 定义 Nginx 运行的用户和用户组
user nginx nginx;

# 根据 CPU 的内核数生成等数量的工作进程
worker_processes    auto;
# 工作进程的 CPU 绑定由 Nginx 自动调整
worker_cpu_affinity    auto;
# 一个 Nginx 进程打开的最多文件描述符数目
worker_rlimit_nofile    65535;

# 在 Main 区块中全局配置

error_log    logs/error.log  error;

# 设置 pid 文件的存放路径
pid    logs/nginx.pid;
```