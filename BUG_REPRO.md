# Bug reproduction

## Bug

扫描请求取消后后台仍继续等待并写入任务结果。

## Trigger

在项目根目录执行：

```bash
go test ./internal/application -run ^TestCanceledScanStopsBeforePersist$ -count=1
```

## Error

目标测试稳定失败，首先出现 `error=<nil>, want context.Canceled`；取消信号没有向延迟保存链路传播，任务结果仍可能落库。容器内连续运行 20 次均可复现。
