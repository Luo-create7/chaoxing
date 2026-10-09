# 学习计划：超星学习通自动刷课项目（chaoxing）

> 本文件是**唯一进度权威来源**。每次课结束必须更新本文件的「进度表」和「课程记录」，并 `git commit + push` 同步到云端仓库。
> 任何新对话开始时，先读本文件确认进度，再继续下一次课。

## 一、项目信息

- 云端仓库：https://github.com/Luo-create7/chaoxing （fork 自 Samueli924/chaoxing，GPL-3.0）
- 本地路径：`D:\Code\chaoxing`
- 运行环境：Python 3.13.13 + pip 26.1.1（已确认，满足项目要求 Python 3.13+）
- 学习模式：零基础边做边教，每次课只精读一个模块，边读边解释语法与函数

## 二、学习目标（已定）

**总目标：学到「阶段4」——能独立给项目加一个小功能。**

| 能力级别 | 具体表现 | 对应阶段 |
|---|---|---|
| 看懂 | 能讲清每个模块的职责和整体调用链 | 阶段1~3 |
| 能改 | 会改 config.ini 配置、能定位并修小 bug | 阶段3 |
| 能加 | 新增一个题库 provider 或新任务类型处理，写测试并推送 GitHub | 阶段4 |

## 三、学习路线与进度表

每次课 60~90 分钟，每周 2~3 次，共约 12 次课（4~6 周）。状态：`待开始 / 进行中 / 已完成`。

| 阶段 | 内容要点 | 课次 | 状态 | 完成日期 |
|---|---|---|---|---|
| 阶段0 跑起来 | 装依赖、复制 config.ini、`python main.py` 跑通 | 第1次 | 待开始 | - |
| 阶段1 语法补课 | 枚举/dataclass/类型注解/match-case、装饰器、抽象类、单例、threading 线程、queue 队列 | 第2~4次 | 待开始 | - |
| 阶段2 爬虫与反爬 | requests 会话/Cookie、AES 加密（cipher.py）、MD5 签名（get_enc）、字体反爬（cxsecret_font）、验证码（captcha）、限速重试（RateLimiter/tenacity） | 第5~7次 | 待开始 | - |
| 阶段3 核心精读 | main.py（入口）→ base.py（主引擎）→ decode.py（解析）→ answer.py（题库） | 第8~10次 | 待开始 | - |
| 阶段4 动手实战 | 加一个小功能（新题库 provider / 新任务处理）、写 pytest 测试、git 提交推送云端仓库 | 第11~12次 | 待开始 | - |

## 四、课程记录（每次课后在此追加）

| 日期 | 课次 | 本次内容 | 掌握情况 | 遗留疑问 |
|---|---|---|---|---|
| - | - | - | - | - |

## 五、学习约定（必须遵守）

1. 术语首次出现先解释；零基础大白话；结构精确紧凑，避免过度冗长列表。
2. 边做边教：解释每步目的、陌生语法和函数作用；不接受只甩代码。
3. 附免费资源链接。
4. 涉及用学习通真实账号实测之前，先询问用户确认。
5. 推送云端仓库（git push）之前，先与用户确认推送内容。
6. 用户决策原则：AI 先给推荐和理由，用户拍板。

## 六、免费学习资源

- Python 官方教程（中文）：https://docs.python.org/zh-cn/3/tutorial/
- requests 文档：https://requests.readthedocs.io/zh-cn/latest/
- Python 多线程（廖雪峰教程）：https://liaoxuefeng.com/books/python/thread/
- 正则表达式入门：https://www.runoob.com/regexp/regexp-tutorial.html
- Git 教程（菜鸟）：https://www.runoob.com/git/git-tutorial.html
- 本项目源码（已克隆到本地，随时可读）

## 七、项目代码地图（已通读，供参考）

```
D:\Code\chaoxing
├── main.py            # 入口：参数解析 → 配置 → 登录 → 课程 → 多线程调度（约640行）
├── app.py             # Celery+Flask 可选任务队列（主流程暂不涉及）
├── config_template.ini # 配置模板（账号/课程/倍速/题库/通知）
├── api/               # 核心包
│   ├── base.py        # Chaoxing 主引擎：登录/章节/视频上报/测验提交/成绩校验（约1660行）
│   ├── answer.py      # 题库抽象基类 + 8种题库实现（约1930行）
│   ├── decode.py      # HTML/JSON 解析：课程/章节/任务点/题目（约530行）
│   ├── cipher.py      # AES 加密登录参数（43行）
│   ├── cookies.py     # Cookie 保存/读取（35行）
│   ├── notification.py# Server酱/Bark/Telegram 推送（267行）
│   ├── captcha.py     # 验证码识别（ddddocr）
│   ├── live.py / live_process.py  # 直播任务
│   ├── cxsecret_font.py / font_decoder.py  # 字体反爬
│   └── logger.py / config.py / exceptions.py / process.py
├── tests/             # pytest 测试
└── resource/          # 字体映射表等资源
```

## 八、同步说明

- 本文件更新后必须执行：`git add -A && git commit -m "更新学习计划" && git push`
- 若新对话中本文件未出现在工作目录，先 `git pull` 拉取最新。
