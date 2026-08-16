# Bug reproduction

## Bug

SSE 断线续传会漏掉最终完成事件，进度永远停在 99%。

## Trigger

在项目根目录执行：

```bash
go test ./internal/application -run ^TestReplayKeepsTerminalProgress$ -count=1
```

## Error

目标测试稳定失败，关键断言为 `bad replay`；从事件 1 之后续传时，结果没有同时保留 ID 2 的运行事件和 ID 3 的 completed 终态。容器内连续运行 20 次均失败。
