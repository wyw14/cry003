# Bug reproduction

## Bug

扫描结果列表会把另一个扫描源下的任务一起返回，路径隔离失效。

## Trigger

在项目根目录执行：

```bash
go test ./internal/application -run ^TestScanPathStaysWithinRoot$ -count=1
```

## Error

目标测试稳定失败，关键断言为 `scope leak`；返回集合同时含 `Scope: alpha` 与 `Scope: beta`，而调用方只请求了 alpha。容器内连续运行 20 次均失败。
