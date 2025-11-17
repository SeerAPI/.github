<div align="center">

# SeerAPI

**赛尔号游戏数据开放平台**

[![GitHub](https://img.shields.io/badge/GitHub-SeerAPI-blue?logo=github)](https://github.com/SeerAPI)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://python.org)

为赛尔号游戏开发者提供标准化、结构化的游戏数据 API 服务</br>
~~完整文档还没写好，凑合看吧~~

</div>

---

## 📖 项目特性

- 🎯 **标准化游戏数据**：分析赛尔号三平台（Flash、HTML5、Unity）的客户端数据，整理为统一的标准格式
- 🌐 **开放数据访问**：通过 RESTful API 为开发者提供便捷的数据访问接口，并提供官方客户端库
- 🛠️ **工具链生态**：构建完整的数据处理工具链，从资源提取到 API 服务
- 🤝 **社区驱动**：这是一项庞大且需要持续维护的项目，欢迎社区贡献解析器、数据补丁和工具改进

## 📦 核心仓库

### 🔧 数据处理工具

| 仓库 | 描述 | 技术栈 | 状态 |
|------|------|--------|------|
| [**Solaris**](https://github.com/SeerAPI/solaris) | 核心数据解析/整理工具，支持三平台数据解析 | Python | ✅ 活跃 |
| [**Albi0**](https://github.com/SeerAPI/albi0) | 插件化的 Unity 游戏资源提取工具 | Python | ✅ 稳定 |

### 📚 数据与模型

| 仓库 | 描述 | 技术栈 | 状态 |
|------|------|--------|------|
| [**seerapi-models**](https://github.com/SeerAPI/seerapi-models) | 标准数据模型和 ORM 定义 | Python, Pydantic | ✅ 活跃 |
| [**config-sources**](https://github.com/SeerAPI/config-sources) | 赛尔号客户端源数据仓库 | 数据文件 | ✅ 自动 |
| [**patch-sources**](https://github.com/SeerAPI/patch-sources) | 数据补丁，用于修复源数据中的错误 | 补丁文件 | ✅ 维护中 |
| [**seer-unity-assets**](https://github.com/SeerAPI/seer-unity-assets) | 赛尔号 Unity 端静态资源节选 | Unity 资源 | ✅ 自动更新
| [**api-data**](https://github.com/SeerAPI/api-data) | 处理后的 API 数据仓库 | JSON+Schema+DB | ✅ 自动更新 |

### 🌐 API 服务

| 仓库 | 描述 | 技术栈 | 状态 |
|------|------|--------|------|
| [**eo-seerapi**](https://github.com/SeerAPI/eo-seerapi) | 部署在腾讯云 EdgeOne Pages 的 API 服务 | TypeScript | ✅ 运行中 |

### 📱 客户端 SDK

| 仓库 | 描述 | 技术栈 | 状态 |
|------|------|--------|------|
| [**seerapi-python**](https://github.com/SeerAPI/seerapi-python) | 官方 Python 客户端库 | Python 3.10+, httpx | ✅ 活跃 |

### ⚙️ 自动化

| 仓库 | 描述 | 技术栈 | 状态 |
|------|------|--------|------|
| [**data-update-workflows**](https://github.com/SeerAPI/data-update-workflows) | 数据更新自动化工作流 | Python, GitHub Actions | ✅ 运行中 |

## 🚀 快速开始

### 使用 Python SDK

安装客户端库：

```bash
pip install seerapi
```

使用示例：

```python
import asyncio
from seerapi import SeerAPI, PageInfo

async def main():
    async with SeerAPI() as client:
        # 获取单个精灵信息
        pet = await client.get('pet', id=1)
        print(f"精灵名称: {pet.name}")
        
        # 获取所有前十个精灵信息
        async for pet in client.paged_list('pet', PageInfo(offset=0, limit=10)):
            print(f"ID: {pet.id}, 名称: {pet.name}")

asyncio.run(main())
```

## 🎯 数据类型

SeerAPI 提供 **50+ 种游戏资源类型**，包括但不限于：

- 🐾 **精灵**：精灵基础信息、属性、种族值、可学习的技能等
- ⚔️ **技能**：技能效果、威力、PP 值，效果描述/ID/参数等
- 🎒 **道具**：物品分类、描述
- 🛡️ **装备**：装备属性、套装效果
- 💎 **刻印**：刻印效果、宝石等
- 🌟 **特性**：精灵特性、特质等
- 📜 更多资源请查看[API 根目录索引](https://api.seerapi.com/v1/)，文档补充中...

每个资源类型都有对应的Schema定义，访问[https://api.seerapi.com/v1/schemas/{resource_name}/$id](https://api.seerapi.com/v1/schemas/{resource_name}/$id)查看。
## 🤝 贡献

我们欢迎所有形式的贡献！

### 如何贡献

1. **添加解析器**：Solaris 需要更多的数据解析器
   - Fork [Solaris](https://github.com/SeerAPI/solaris) 仓库
   - 在 `solaris/parse/parsers/` 下添加新解析器
   - 提交 Pull Request

2. **修复数据错误**：发现源数据错误？
   - 在 [patch-sources](https://github.com/SeerAPI/patch-sources) 提交补丁

3. **改进文档**：帮助我们完善文档和示例

4. **报告问题**：在相应仓库提交 Issue

## 📜 许可证

SeerAPI 的大部分项目采用 **MIT License** 开源。

具体许可信息请查看各仓库的 LICENSE 文件。

## ❤️ 特别鸣谢

- [@HurryWang](https://github.com/WhY15w) 和他的 [赛尔号信息聚合页](https://seerinfo.yuyuqaq.cn/)
- [@火火](https://github.com/Yogurt114514) 在数据分析过程中提供的帮助
- 所有的赛尔号开源开发者们
