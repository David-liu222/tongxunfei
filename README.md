# 通讯费报销整理 Skill

这个仓库保存 Codex skill：`communication-fee-reimbursement-organizer`，用于整理力量煤业电话费/通讯费报销资料。

## 功能

这个 skill 帮助 Codex 按模板处理：

- 通讯费/电话费报销制度
- 人力资源名单表
- 公司通讯录和煤矿通讯录 PDF
- 电话费发票、发票金额或账期资料
- Word 或 Excel 通讯费报销模板

输出内容包括：

- 按模板填写好的通讯费报销文件
- 按每人每月拆分的发票金额和实报金额
- 发票开票信息核对结果
- 发票电话号与通讯录电话号不一致说明
- `需人工确认的问题`异常清单

## 内置通讯录

skill 已内置用户确认上传的 2026 年 4 月通讯录引用文件：`references/address-books-2026-04.md`。

- 公司通讯录：77 条
- 煤矿通讯录：90 条
- 合计：167 条
- 缺手机号：0 条

如果后续提供新版通讯录，应优先使用新版，并把内置通讯录作为历史对照。

## 内置模板

skill 已内置用户确认上传的 Word 模板：`assets/templates/通讯费第1季度.docx`。没有另传新版模板时，使用这个模板的副本进行填报，不能直接修改模板原件。

## 内置工作簿

skill 已内置用户确认上传的 Excel 数据资产，说明见：`references/bundled-workbooks.md`。

- `assets/data/2026年：电话费、燃油费报销人员统计.xlsx`
- `assets/data/1.人力资源报表- 20260611-力量煤业_副本.xlsx`

如果后续提供新版 HR 名单或电话费/燃油费台账，应优先使用新版，并把内置工作簿作为历史对照。

## 本地安装

把 skill 文件夹复制到 Codex skills 目录：

```bash
mkdir -p ~/.codex/skills
cp -R communication-fee-reimbursement-organizer ~/.codex/skills/
```

重启 Codex 或开启新线程后即可使用。

## 使用示例

```text
使用 communication-fee-reimbursement-organizer 根据制度、人员名单、两个通讯录、发票金额和通讯费模板整理通讯费报销资料。
```

## 注意

- 保留用户提供的模板格式，不随意调整表格样式、合并单元格、签字栏或公式。
- 发票购买方信息、手机号、人员和金额差异要单独列入异常清单。
- 涉及 HR、发票和通讯录资料时，默认只做本地处理，不上传原始资料到外部 OCR 或第三方服务。
