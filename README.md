# dsh-collection（DeepSeek Harness 插件与 Skill 合集）

一个集中管理 **DeepSeek Harness** 插件和 Skill 的仓库：每个项目保持独立仓库（可单独 `dsh plugin add` 安装），这里通过 **git submodule** 统一收纳并分类展示。
<br>

> ⭐ **如果这些插件帮到了你，欢迎给项目点个 Star！** 你的支持是我持续维护的动力 🙏
> 
> ⭐ **If these plugins helped you, please Star the repos!** Your support keeps me improving them 🙏

## 插件（Plugins）

插件是 npm 包 + `dsh.bundle` 声明，可一键安装。每个插件保持独立仓库（根目录即包），本仓库以 submodule 引用。

| 插件 | 说明 | 安装 |
|---|---|---|
| [**dsh-plugin-organizer**](./plugins/dsh-plugin-organizer) | 插件列表按 **官方 / 第三方** 分组收纳，可展开/折叠 | `dsh plugin --profile web add Inspireason/dsh-plugin-organizer` |
| [**dsh-skill-organizer**](./plugins/dsh-skill-organizer) | Skill 列表按 **自动推荐分类 + 手动调整** 分组收纳 | `dsh plugin --profile web add Inspireason/dsh-skill-organizer` |

### 安装全部插件

```sh
# 方式一：逐个安装（推荐，安装后重启 DSH 并硬刷新）
dsh plugin --profile web add Inspireason/dsh-plugin-organizer
dsh plugin --profile web add Inspireason/dsh-skill-organizer

# 方式二：先克隆本仓库再通过本地路径安装
git clone --recurse-submodules https://github.com/Inspireason/dsh-collection.git
dsh plugin --profile web add ./dsh-collection/plugins/dsh-plugin-organizer
dsh plugin --profile web add ./dsh-collection/plugins/dsh-skill-organizer
```

> 两个插件都声明了 `dsh.bundle.patch`，`dsh plugin add` 会自动挂载到 `dsh.profile.bundles`。
> 若 profile 之前手动挂载过（`cordis.patch.yml` 里有对应 id 的行），先删除避免双挂载。

## Skill（Skills）

> 计划中：后续会将 `~/.dsh/skills/` 中的轻量 Skill 收录到本仓库的 `skills/` 目录，
> 通过 junction / customSkillDirs 让 DSH 直接扫描。当前暂未收录。

## 仓库结构

```
dsh-collection/
├── README.md                      # 本目录页
├── plugins/                       # 插件 submodules
│   ├── dsh-plugin-organizer/       # → github.com/Inspireason/dsh-plugin-organizer
│   └── dsh-skill-organizer/        # → github.com/Inspireason/dsh-skill-organizer
└── skills/                        # （预留）Skill 目录
```

## 更新子模块

```sh
git submodule update --remote --merge
```

## License

各插件/技能保留其独立仓库的许可证；本仓库索引部分为 MIT。
