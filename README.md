# 大G的闲鱼运营skill

用一个 Codex Skill 串起闲鱼选品、上品、关键词回复和付款后发货。可以处理一批商品，也可以拿着已有商品 ID，只做回复、发货或对账。

**装好就能用本地资料做选品分析、上架草稿和绑定表。** 实时发布、回复和发货需要另行接入账号已开通、且获闲鱼许可的在线服务。

## 安装

在 Codex 里发送这句话：

```text
用 $skill-installer 安装 GitHub 仓库 Kujepan/dag-xianyu-operations-skill
的 skills/xianyu-operations 目录。
```

也可以下载仓库，把完整的 `skills/xianyu-operations` 文件夹复制到项目的 `.agents/skills/`，或个人的 `~/.agents/skills/`。安装后的路径末尾是 `xianyu-operations/SKILL.md`。如果 Codex 没显示新技能，重启后再试。 [OpenAI Docs 的 Skill 安装说明](https://learn.chatgpt.com/docs/build-skills#where-codex-loads-local-skills)

## 第一次用

准备一件商品的标题、价格、主图和描述，附上你已有的关键词样本或任务卡。需要自动回复时，加上常见问题和对应答案。需要发货时，写明买家会收到什么、如何领取。

例如，把你自制的打印清单 PDF 和主图交给 Codex，再发：

```text
用 $xianyu-operations 为我自制的每周计划表 PDF 准备闲鱼商品草稿，定价 1.99 元。
用我附上的主图。买家收到一份 A4 可打印 PDF。
固定回复：「怎么打印」→「用 A4 纸按实际大小打印」。
请给我上架文案、回复规则和付款后交付说明，先做草稿。
```

拿到草稿后，核对类目、标价和交付内容。商品上线后，把商品 ID 交给 Skill，即可继续准备或核对该商品的绑定。

## 每一步怎么用

| 环节 | 给 Codex 什么 | 核对什么 |
| --- | --- | --- |
| 选品 | 关键词、市场样本或导出数据 | 候选商品、样本范围、挂牌价和数据缺项 |
| 上品 | 标题、真实类目、售价、主图和详情 | 草稿字段。实际发布后回查标题、商品 ID、链接和状态 |
| 自动回复 | 商品 ID、关键词、已确认的固定话术 | 商品与关键词一一对应，未命中的咨询有人工处理口径 |
| 自动发货 | 商品 ID、交付内容、领取步骤 | 付款后触发、发给对应订单、同一订单只发一次 |

如果你已经上架，也可以直接发：

```text
用 $xianyu-operations 核对这两件已上架商品。
按我提供的商品 ID、关键词话术和交付内容逐项比对，标出缺失或串绑的规则。
```

## 在线执行和验收

1. 在已获授权的服务中确认目标账号和可用能力。选定数字商品类目后，按该类目支持的入口交付。 [闲鱼社区法律声明](https://terms.alicdn.com/legal-agreement/terms/suit_bu1_taobao/suit_bu1_taobao202103061039_91765.html)
2. 商品上线后，从发布列表回查商品 ID。按同一个 ID 逐件绑定关键词回复和交付内容，再打开配置页核对生效状态。
3. 首笔实际订单付款后，核对订单状态、发出的交付内容和平台显示的发货状态。验收记录分别填写「配置已核对」和「真实订单已履约」。

更多字段与接入参考见 [配置与核验](skills/xianyu-operations/references/workflow.md)。

本项目采用 [MIT 许可证](LICENSE)。
