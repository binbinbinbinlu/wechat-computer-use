# WeChat Computer Use Skill

让 ChatGPT/Codex 使用已有的 Windows computer-use 能力操作桌面微信。

这是一份由实际操作测试总结出的 Agent Skill，当前验证环境是 Windows、Weixin 4.2.0.12、英文界面。它提供操作流程和恢复经验，不包含独立自动化运行时，也不读取或解密微信数据库。

## 前提

- Windows 上已安装微信/Weixin。
- 当前 Codex 环境已安装并可使用 computer-use 技能。
- 微信登录、扫码和手机身份确认按当前用户授权及环境要求处理。

## 安装

将本仓库放入你自己的 Codex skills 目录，目录名为 `wechat-computer-use`，不要覆盖已有的个人修改。例如：

```powershell
git clone https://github.com/binbinbinbinlu/wechat-computer-use.git "$env:USERPROFILE\.codex\skills\wechat-computer-use"
```

下一轮对话可以说：

> 使用 $wechat-computer-use，先检查微信界面，只做只读测试。

## 已验证

- 联系人部分姓名搜索、区分个人/群/历史结果、切换聊天。
- 打开独立聊天记录窗口、关键词搜索、无结果识别、媒体筛选、日期浮层与有限距离滚动。
- 仅在用户明确确认的本人聊天：中英文、数字、标点、Unicode 表情、点击 Send 发送、Ctrl+Enter 换行。
- 草稿在切换聊天后保留；只清除测试时自己创建的草稿。
- 点击聊天区域正常空白位置关闭 Chat Info 侧栏。

## 当前限制

- 一次操作后的首个快照可能仍是旧界面，需要再次观察；不要盲目重复发送。
- 点击需要有效截图几何信息；旧元素索引不能跨状态复用。
- Escape 不是可靠的微信通用关闭键；测试曾出现主窗口消失，根因未确定。
- 原生附件选择窗口的控件索引与焦点反馈存在问题；目前只验证了打开和取消，没有验证附件发送。
- 未验证完整历史导出、后台操作、跨版本稳定性或所有输入法设置。
- 客户端出现气泡不代表对方已收到或已读。

## 文件

- [SKILL.md](SKILL.md)：技能入口。
- [navigation.md](navigation.md)：界面定位与恢复。
- [history.md](history.md)：聊天记录搜索与筛选。
- [sending.md](sending.md)：本人写入测试与发送注意事项。
- [test-results.md](test-results.md)：去标识化测试证据与未测范围。

## 一起完善

欢迎通过 Issues 描述复现步骤、客户端版本、界面语言、预期与实际行为；通过 Pull Requests 提交改进。请使用合成示例，去除联系人、聊天正文、账号、凭据和截图中的私人资料。不要把某次用户授权写成所有用户的默认许可。

这个项目是在对比现有微信自动化方案后独立整理的 computer-use 工作流，不打包其他项目的 Python 源码。测试以小步操作和结果复核为主，不承诺无人值守或批量群发。
