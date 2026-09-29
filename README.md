# skill-matcher

> 让 AI 在动手之前，先想清楚该用哪把工具。

一个 WorkBuddy / Claude Code **技能（Skill）**：在你下达任务之后、AI 开始执行之前，自动扫描已安装的全部技能、判断相关度，选出最合适的那个——能自动就用，有歧义就问，没对口就闭嘴干活。

## 解决的问题

技能装多了会出现两种浪费：

- **漏用** —— 明明装了处理 PDF 的技能，却手写脚本硬解。
- **噪音** —— 每次任务都汇报"我扫描了 40 个技能，发现 3 个相关……"，用户被迫读调度日志。

这个技能把匹配做成一个**安静的前置步骤**：只在结论会改变执行方式时才开口。

## 装上之后会看到什么

| 你说 | 它会做 |
|---|---|
| 「把 report.pdf 按章节拆开」 | 一句「用 pdf 处理：…」，然后调用 |
| 「做个季度复盘，要有图表」 | 列出 Word / PPT / 图表三个候选，各带理由，等你选 |
| 「把这段文字的错别字改一下」 | 什么都不说，直接改 |
| 「把这个 .psd 按图层导出」 | 一句「现有技能里没有对口的，我直接做」 |
| 「你好」 | 什么都不说（不触发匹配） |

## 安装（30 秒）

把 `skill-matcher/` 整个目录放进你的技能目录即可，**无需重启**，下次会话就会出现在技能清单里：

| 系统 | 目标路径 |
|---|---|
| macOS / Linux | `~/.workbuddy/skills/skill-matcher/` |
| Windows | `C:\Users\<你>\.workbuddy\skills\skill-matcher\` |

```bash
git clone --depth 1 https://github.com/teenvision/skill-matcher.git /tmp/skill-matcher
cp -r /tmp/skill-matcher/skill-matcher ~/.workbuddy/skills/
```

验证：对 AI 说一句「用 skill-matcher 处理这个任务」，能加载就说明装好了。

## 三条设计底线

1. **产出物优先** —— 先问"要做出来的东西是什么"，再找技能；不看关键词字面重合。
2. **直调三条件** —— 高相关 **且** 唯一 **且** 不改变执行方式，三者缺一不可。
3. **输出只有三档** —— 确认块 / 一句话 / 零输出。没有第四种。

## 目录

```
本仓库
└── skill-matcher/                    # 技能本体：把这个目录拷进你的 skills 目录
    ├── SKILL.md                     # 技能主体：定位、触发条件、匹配流程、输出规范
    ├── references/
    │   └── matching-examples.md     # 打分样例集 + 回归测试用例
    ├── README.md                    # 详细说明
    └── LICENSE
```

完整行为说明、边界与适配指引见 [skill-matcher/README.md](./skill-matcher/README.md)。

## 许可

MIT © teenvision
