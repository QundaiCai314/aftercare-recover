# aftercare-recover 1.0.0

售后助手第七个 Skill：依据失败事件、页面证据与操作台账，提出一次有限恢复计划。

先区分未发出、已证明无业务效果、结果未知及已核实成功。未知结果优先查记录，不能重新上传、提交、撤销、预约或发送。Skill不操作浏览器、不循环重试、不修改用户目标或授权、不清空预算台账，也不启动Spark。

## 下载

- [可加载 Skill 包](aftercare-recover-1.0.0.zip)：解压后使用 `aftercare-recover/`。
- [完整工程交付](aftercare-recover-1.0.0-full.zip)：含Skill、合成样例、校验代码、随机页面数据测试、报告和未生效契约提案。
- [测试报告](测试报告.md)
- [契约修订提案](契约修订提案.md)
- [SHA-256摘要](SHA256SUMS.json)

中央契约仍为1.0.0，输出RecoveryPlan；completed只表示分析完成。后续恢复由主Agent、页面操作Skill、执行层和结果核对共同落实。

## 验证与限制

41个作者编写场景、9个契约/语义反例和Skill Creator结构校验通过；40个随机页面数据变体的测试替身检查通过。这些不是模型前向测试、真实浏览器端到端测试或实际售后恢复成功率。

生产执行服务、平台适配器、持久预算/去重、授权与互斥仍需宿主实现。校验器不会执行或授权；宿主语义见证必须由独立可信来源建立。未知业务效果不因更换提案ID解除。

## 复现

完整包解压后，使用Python及`aftercare-recover/scripts/requirements.txt`中的依赖：

```text
python -B -X utf8 tests/run_tests.py
python -B -X utf8 tests/run_randomized.py
python -B -X utf8 tests/check_package.py
```

源文件摘要核对仅在对应外部参考文件可用时执行。公开副本不含作者机器路径，`source-audit.json`和provenance中的external-source是来源标识，不是随包提供的权威原文件；缺失源文件核对不记为通过。包内派生Schema可独立用于结构校验。

随机种子及真值仅供评测器使用，未来模型测试必须隔离`tests/evaluator-only-variants.json`和生成器。实际成功率、误操作及人工介入未测，保持null；不把测试代码零外部动作当生产安全证据。

发布副本去除本机路径并重新生成摘要；未修改原交付、其他Skills或中央契约，未安装到全局。资料均为合成开发案例，不含真实订单、账户或售后凭证。
