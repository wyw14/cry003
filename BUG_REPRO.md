# Bug reproduction

## Bug

同一个扫描请求并发重试时会启动多个执行实例并生成不同任务 ID。

## Trigger

在项目根目录执行：

```bash
go test ./internal/application -run ^TestOnlyOneScanExecution$ -count=1
```

## Error

目标测试稳定失败，关键断言为 `idempotent requests returned different IDs`（并可能继续显示 `stored N items, want 1`）。Go 1.24 Linux 容器内加 `-race` 连续运行 20 次均失败。
