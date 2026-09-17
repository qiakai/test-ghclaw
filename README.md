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

- [x] PushEvent — git push（注意: feed 延迟可达 10 分钟+）
- [x] IssueCommentEvent — issue/PR 下评论
- [x] IssuesEvent — 开/关 issue
- [x] PullRequestEvent — 开 PR / 合并 PR
- [x] PullRequestReviewEvent — 提交 review（COMMENT 类型；不能 approve 自己的 PR）
- [x] PullRequestReviewCommentEvent — diff 行内评论
- [x] ReleaseEvent — 发布 release
- [x] DeleteEvent — 删分支
- [x] WatchEvent — star 本仓库
- [x] PublicEvent — 仓库转 public
- [ ] CreateEvent — 建分支/tag（分支创建先于监听启动被当历史跳过；tag 创建的 feed 延迟超长，待补）
- [x] GollumEvent — wiki 编辑
- [ ] ForkEvent — fork 本仓库（需要第二个账号/组织）
- [ ] MemberEvent — 添加协作者（需要第二个账号）
batch1: Thu Sep 17 19:23:46 CST 2026
ab-test: Thu Sep 17 19:28:53 CST 2026
retry: Thu Sep 17 19:29:59 CST 2026
