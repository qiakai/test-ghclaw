# test-ghclaw

ghclaw 的测试沙盒仓库。

两个用途：

1. **受控产生事件** — 在这里执行动作（push / 开 issue / 评论 / 开 PR / review /
   发 release / 建删分支 / star / fork / 开 wiki），为 ghclaw 提供各类型
   GitHub events 的实时测试数据源
2. **存放整理后的事件样本** — `testdata/events/` 保存从 ghclaw 运行时捕获的
   真实单事件 JSON（每类型精选样本，非全量），用于：

   - 了解每种事件类型实际能获取到的字段
   - 作为 events.awk / 下游分发逻辑的离线测试 fixture
   - 指导 MQ.tsv 列设计与 agent 上下文裁剪

注意：`testdata/` 放的是**精选样本**，运行时全量数据在监听机器的
`$X_CMD_ROOT_TMP/ghclaw/events/data/` 下，不同步进本仓库。

事件类型清单（产生方式见各类型文档需求）：

- [x] PushEvent — git push
- [x] IssueCommentEvent — issue/PR 下评论
- [ ] IssuesEvent — 开/关 issue
- [ ] PullRequestEvent — 开/关/合并 PR
- [ ] PullRequestReviewEvent — 提交 review
- [ ] PullRequestReviewCommentEvent — diff 行内评论
- [ ] ReleaseEvent — 发布 release
- [ ] CreateEvent / DeleteEvent — 建删分支或 tag
- [ ] WatchEvent — star 本仓库
- [ ] ForkEvent — fork 本仓库
- [ ] GollumEvent — wiki 编辑
- [ ] MemberEvent — 添加协作者
