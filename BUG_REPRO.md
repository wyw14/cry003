# Bug reproduction

## Bug

任务提交中途失败后状态已经变成 running，但执行记录没有落下。

## Trigger

在项目根目录执行：

```bash
go test ./internal/application -run ^TestFailedScanCommitKeepsQueuedState$ -count=1
```

## Error

目标测试稳定失败，关键断言为 `partial commit`；错误返回后快照的 State/Version 已变化，而 Secondary 仍未提交。容器内连续运行 20 次均可复现。
