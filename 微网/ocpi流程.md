## 一、当前资料整理

**1. 官网 https://evroaming.org/ocpi/ — 权威发布** EVRoaming就是ocpi维护组织，开发管理维护

**2. 开源 https://github.com/ocpi/ocpi — 协议源码**
- 定位：OCPI 协议源码仓库，`tag v2.2.1-d2` 与官网 PDF 同版
```
  ✓ Credentials handshake
  ✓ Location push
  ✓ EVSE status push
  ✓ Tariff
  ✓ Token authorization
  ✓ START_SESSION
  ✓ STOP_SESSION
  ✓ Session push
  ✓ CDR push
```

## 二、工作

**结论：需新增独立服务，对齐协议并打通现有链路**

| 项 | 内容 | 说明 |
|---|---|---|
| **需要新增模块** | `jdy-saas-ocpi-service` | 当前项目是jdk8，ocpi2.2.1需要jdk17 |
| **对齐协议** | OCPI 2.2.1 CPO 侧 8 个 yaml | `Versions` + `Credentials` 握手；`Locations`(Sender) / `Tariffs`(Sender) / `Tokens`(Receiver) / `Commands`(Receiver: START/STOP) / `Sessions`(Sender) / `CDRs`(Sender) |
| **对接现有** | OCPP 1.6 + 业务模块 | 需在新模块做整合，但 **OCPI 只取结果，不照搬 CPO 内部逻辑**。 |

## 三、开发后流程（到上线）

1.  **自测：** 同现有子睿测试方式，肯定是以“能完整充一单”为准 — 先本地/工厂桩联调，再到英国场站实桩复测，2.2.1 接口同步做校验。
2.  **联调：** 接入英国 Hub（Gireve / EcoMovement / Hubject，相当于支付宝），用测试环境与对方 EMSP(管理司机，所有app；相当于漫游) 真实跑一单。
3.  **拿证/合规验证：** 英国法条强制 2.2.1，非可选证书；OCPI 官方 Compliance Tool 自验证 + Hub 出具的**互通报告**作为合规证据。
4.  **上线：** xx 网关切可信证书，`https://cpo.xrenewable.com/ocpi/versions` 对外可通，推送监控（成功率/延迟）上线。
5.  **商家接入：** 首批选 1-2 个自有站/合作商户试点，验证漫游计费与对账（`finance_merchant_bill` 对 `CDR total_cost_incl_vat`），后再批量开放。
6. **最后用户**：我们场站 → 推 Location 给 Hub → Hub 转给所有 EMSP → 司机在自己常用的 App 里可以搜索到我们的场站
## 待确定
- 是不是至少有一个商家接入才能拿证，HUB验收标准
- 其他的可能要开发过程中才能发现

## 结论
- 最后金总说是不需要走hub，让另一家第三方公司干嘛干嘛