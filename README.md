# 医晓 HospitalAgent

面向新加坡夜间症状场景的智能自我分诊与就医导航原型。

本仓库仅保留应用源码、规则、测试、Agent 提示词、运行所需知识库和部署配置；答辩 PPT、预览图片、比赛说明及证明材料均未包含。

## 目录

- `patient_ui/`：无需构建的患者端静态应用
- `rule_engine/`：Python 规则引擎、JS 对拍测试与规则定义
- `prompts/`：六个 Agent 的提示词源码
- `knowledge_base/`：患者安全、导航和临床参考知识库
- `test_cases/`：端到端导航测试数据
- `deploy/`：Nginx 配置

## 本地运行

```bash
python -m http.server 8080 --directory patient_ui
```

浏览器打开 `http://localhost:8080`。默认使用浏览器内置的规则引擎镜像，不依赖后端服务。

## Docker 部署

```bash
docker build -t hospitalagent .
docker run -d --name hospitalagent -p 8080:80 --restart unless-stopped hospitalagent
```

浏览器打开 `http://服务器IP:8080`，健康检查地址为 `/healthz`。

## 测试

```bash
python rule_engine/run_tests.py
node rule_engine/parity_test.js
```

> 本项目用于分诊与就医导航演示，不构成医疗诊断。真实使用前须完成临床审核、隐私评估和当地监管合规审查。

