---
title: "Release Notes for 3.1.0"
keywords: "Kubernetes, KubeSphere, release-notes"
description: "KubeSphere Release Notes for 3.1.0"

linkTitle: "Release Notes - 3.1.0"
weight: 50
---

## 如何获取 v3.1.0

- [Install KubeSphere v3.1.0 on Linux](https://github.com/kubesphere/kubekey)
- [Install KubeSphere v3.1.0 on existing Kubernetes](https://github.com/kubesphere/ks-installer)

# Release Notes

## 新功能及增强
### 集群管理
 - member 集群管理服务轻量化，移除 redis、ldap 等组件 [#3056](https://github.com/kubesphere/kubesphere/issues/3056)
 - 简化添加集群的操作，并验证集群配置（如 jwtSecret）有效性 [#3232](https://github.com/kubesphere/kubesphere/issues/3232)
 - 可按需配置集群控制器同步时间段 [#3213](https://github.com/kubesphere/kubesphere/issues/3213)
 - 重构集群控制器，优化逻辑  [#3234](https://github.com/kubesphere/kubesphere/issues/3234)
 - 支持以高可用方式运行 Tower 管理和代理服务 [#31](https://github.com/kubesphere/tower/issues/31)
 - 升级工具箱中的 Kubectl 且与 Kubernetes 集群版本保持一致 [#3103](https://github.com/kubesphere/kubesphere/issues/3103)

#### 边缘节点管理
##### 集成 KubeEdge [#3070](https://github.com/kubesphere/kubesphere/issues/3070)

 - 支持 KubeEdge 云端组件的安装部署
 - 支持 KubeEdge 边缘节点的添加
 - 支持边缘节点的日志和监控数据采集
 - 支持边缘节点网络配置自动化的加入和退出
 - 边缘节点在加入集群时，支持自动添加污点
 - 支持通过添加节点选择器的方式禁止云端工作负载(如 Daemonset)调度到边缘节点
- 支持调度工作负载至边缘节点

### 认证和权限管理
 - 新用户首次登录，可修改预分配的密码
 - 通过第三方平台登录 KubeSphere，需确认账户信息
 - 支持 [CAS](https://apereo.github.io/cas/5.0.x/protocol/CAS-Protocol-Specification.html) 标识提供者 [#3047](https://github.com/kubesphere/kubesphere/issues/3047)
 - 支持 [OIDC](https://openid.net/specs/openid-connect-core-1_0.html) 标识提供者 [#2941](https://github.com/kubesphere/kubesphere/issues/2941)
 - 支持 IDaaS(Alibaba Cloud Identity as a Service) 标识提供者 [#2997](https://github.com/kubesphere/kubesphere/pull/2997)
 - 支持 Service Account 管理，可给 Service Account 分配角色 [#3211](https://github.com/kubesphere/kubesphere/issues/3211)
 - 改善与 LDAP 标识提供者的集成，支持 LDAPS 和搜索过滤（search filter）[#2970](https://github.com/kubesphere/kubesphere/issues/2970)
 - 改善标识提供者插件，简化标识提供者的配置 [#2970](https://github.com/kubesphere/kubesphere/issues/2970)


### 多租户管理
 - 支持用户组管理，可邀请指定用户组至企业空间或者项目 [#2940](https://github.com/kubesphere/kubesphere/issues/2940)
 - 支持企业空间配额，与 Kubernetes 资源配额 [ResourceQuota](https://kubernetes.io/docs/concepts/policy/resource-quotas/) 保持一致，可限制指定企业空间下所有项目所消耗的资源 [#2939](https://github.com/kubesphere/kubesphere/issues/2939)
 - 删除企业空间时，提示是否删除级联资源的，确认后再删除 [#3192](https://github.com/kubesphere/kubesphere/issues/3192)

### 网络
 - 新增支持 Kube-OVN 插件
 - 支持 Calico IP 池管理 [#3057](https://github.com/kubesphere/kubesphere/issues/3057)
 - 支持为 Deployment 指定静态 IP [#3058](https://github.com/kubesphere/kubesphere/issues/3058)
 - 支持网络可视化 [#3061](https://github.com/kubesphere/kubesphere/issues/3061) [#583](https://github.com/kubesphere/kubesphere/issues/583)

### 可观察性
 - 优化集成已有 Prometheus 服务对接方式 [#3068](https://github.com/kubesphere/kubesphere/issues/3068) [#1164](https://github.com/kubesphere/ks-installer/pull/1164) [Guide](https://kubesphere.io/docs/faq/observability/byop/)
 - 升级 Prometheus 至 v2.26.0
 - 升级 kube-state-metrics 至 v1.9.7
 - 升级 Notification Manager 至 v1.0.0 [Releases](https://github.com/kubesphere/notification-manager/releases)
 - 升级 FluentBit Operator 至 v0.5.0 [Releases](https://github.com/kubesphere/fluentbit-operator/releases)
 - 升级 FluentBit 至 v1.6.9

#### 监控
 - 支持图形化方式配置 ServiceMonitor [#1031](https://github.com/kubesphere/console/pull/1301) 
 - 支持 PromQL auto-completion 和 syntax highlighting [#1307](https://github.com/kubesphere/console/pull/1307)
 - 支持集群层级的自定义监控 [#3193](https://github.com/kubesphere/kubesphere/pull/3193)
 - 提供可将 Grafana dashboard 转化为 KubeSphere Dashboard 的工具 [#9](https://github.com/kubesphere/monitoring-dashboard/pull/9)
 - 升级 Prometheus client_golang 至 v1.5.1，升级 Prometheus 至 v1.8.2 [3097](https://github.com/kubesphere/kubesphere/pull/3097)

#### 告警
 - 支持 Prometheus 告警规则管理 [#3181](https://github.com/kubesphere/kubesphere/pull/3181)
 - 支持平台及项目层级的告警规则 [#3181](https://github.com/kubesphere/kubesphere/pull/3181)
 - 支持显示指定告警规则的相关告警 [#3181](https://github.com/kubesphere/kubesphere/pull/3181)

#### 通知管理 
 - 新增 钉钉、 企业微信、Slack、Webhook 通知方式，其提供图形化管理[#3066](https://github.com/kubesphere/kubesphere/issues/3066)

#### 日志
 - 支持将日志输出到 [Loki](https://github.com/kubesphere/fluentbit-operator/blob/master/docs/plugins/output/loki.md) [#39](https://github.com/kubesphere/fluentbit-operator/pull/39)
 - 支持收集 kubelet/docker/containerd 的日志 [#38](https://github.com/kubesphere/fluentbit-operator/pull/38)
 - 支持收集 [auditd](https://github.com/kubesphere/fluentbit-operator#auditd)的日志 [#45](https://github.com/kubesphere/fluentbit-operator/pull/45)

### DevOps
 - 支持 Gitlab 多分支流水线 [#3100](https://github.com/kubesphere/kubesphere/issues/3100)
 - 可同时启动并运行多条流水线 [#1811](https://github.com/kubesphere/kubesphere/issues/1811)
 - 支持流水线复制 [#3053](https://github.com/kubesphere/kubesphere/issues/3053)
 - 新增权限可控的流水线审核机制 [#2483](https://github.com/kubesphere/kubesphere/issues/2483) [#3006](https://github.com/kubesphere/kubesphere/issues/3006)
 - 访问 DevOps 工程首页可查看流水线运行状态 [#3007](https://github.com/kubesphere/kubesphere/issues/3007)
 - 支持通过流水线 Tag 触发流水线运行 [#3051](https://github.com/kubesphere/kubesphere/issues/3051)
 - 支持 S2I Webhook [#6](https://github.com/kubesphere/s2ioperator/issues/6)
 - 优化在输入错误的流水线定时参数时的提示信息 [#2919](https://github.com/kubesphere/kubesphere/issues/2919)
 - 优化创建流水线的交互体验 [#1283](https://github.com/kubesphere/console/issues/1283)
 - 优化 S2I 错误提示信息 [#140](https://github.com/kubesphere/s2ioperator/issues/140)
 - 升级 Jenkins 至 2.249.1 [#2618](https://github.com/kubesphere/kubesphere/issues/2618)
 - 调整 Jenkins 部署方式为 Jenkins distribution [#2182](https://github.com/kubesphere/kubesphere/issues/2182)

### 应用商店及应用
 - 新增 MySQL 高可用集群应用：XenonDB
 - 支持修改已部署的应用模板
 - 支持查看应用模板部署失败的原因 [#3036](https://github.com/kubesphere/kubesphere/issues/3036) [#3001](https://github.com/kubesphere/kubesphere/issues/3001) [#2951](https://github.com/kubesphere/kubesphere/issues/2951) 
 - 支持批量删除应用模板

### 微服务治理
 - 支持图形化流量方向检测，图像化方式显示应用（composed application）流量的流入/流出 [#3153](https://github.com/kubesphere/kubesphere/issues/3153)
 - 支持 Kiali 附加组件，用户可以通过 Kiali直接管理 istio [#3106](https://github.com/kubesphere/kubesphere/issues/3106)
 - 支持 Nginx Ingress Gateway 的监控，新增 nginx ingress controller 的监控指标 [#1205](https://github.com/kubesphere/ks-installer/pull/1205)
 - 支持在创建应用时添加应用路由 [#1426](https://github.com/kubesphere/console/issues/1426) 
 - 升级 istio 至 1.6.10 [#3326](https://github.com/kubesphere/kubesphere/issues/3236)

### 计量计费
 - 支持集群、企业空间和应用级别的应用消耗量统计 [#3062](https://github.com/kubesphere/kubesphere/issues/3062)
 - 通过 ConfigMap 方式可为计量资源配置计费单价

## 重要的技术调整
 - 升级 Kubernetes 版本依赖，从 v1.17 调整至 v1.18 [#3274](https://github.com/kubesphere/kubesphere/issues/3274)
 - 基于 CRD 重构应用管理框架 OpenPitrix 并修复原有架构导致的问题 [#3036](https://github.com/kubesphere/kubesphere/issues/3036) [#3001](https://github.com/kubesphere/kubesphere/issues/3001) [#2995](https://github.com/kubesphere/kubesphere/issues/2995) [#2981](https://github.com/kubesphere/kubesphere/issues/2981) [#2954](https://github.com/kubesphere/kubesphere/issues/2954) [#2951](https://github.com/kubesphere/kubesphere/issues/2951) [#2783](https://github.com/kubesphere/kubesphere/issues/2783) [#2713](https://github.com/kubesphere/kubesphere/issues/2713) [#2700](https://github.com/kubesphere/kubesphere/issues/2700) [#1903](https://github.com/kubesphere/kubesphere/issues/1903) 

## 废弃或移除的功能

## 问题修复
 - 修复容器日志不支持ANSI Color的问题 [#1322](https://github.com/kubesphere/kubesphere/issues/3044)
 - 修复以“kube”起始命名的项目（namespace）下的微服务应用无法获取istio 相关的监控数据的问题 [#3126](https://github.com/kubesphere/kubesphere/issues/3162) 
 - 修复部署工作负载时的 bad_certificate 错误 [#3112](https://github.com/kubesphere/kubesphere/issues/3112)
 - 修复 viewer 可打开容器终端的安全隐患 [#3041](https://github.com/kubesphere/kubesphere/issues/3041)
 - 修复级联资源无法被删除的问题 [#2912](https://github.com/kubesphere/kubesphere/issues/2912)
- 修复 admission webhook 的自签名依赖于 legacy Common Name field 的问题 [#2928](https://github.com/kubesphere/kubesphere/issues/2928)
- 修复微服务应用“监控”按钮无效的问题 [#1394](https://github.com/kubesphere/console/issues/1394)
- 修复灰度发布的服务名不能与微服务应用的标签名相同的问题 [#3128](https://github.com/kubesphere/kubesphere/issues/3128)
- 修复微服务应用状态无法更新的问题 [#3241](https://github.com/kubesphere/kubesphere/issues/3241)
- 修复 host 和 member 集群在有同名企业空间的情况下，member 集群下的企业空间被删除的问题 [#3169](https://github.com/kubesphere/kubesphere/issues/3169)
- 修复通过 proxy 方式下联邦多集群连接断开的问题 [#3202](https://github.com/kubesphere/kubesphere/pull/3203)
- 修正多集群状态显示问题 [#3135](https://github.com/kubesphere/kubesphere/issues/3135)
- 修复依赖于 legacy Common Name field 的证书调用 Webhook 失败的问题 [#2928](https://github.com/kubesphere/kubesphere/issues/2928)
- 修复 DevOps 工程管理员无法下载 artifacts 的问题 [#3088](https://github.com/kubesphere/kubesphere/issues/3083)
- 修复由于用户数据不一致导致的无法创建流水线的问题 [#3105](https://github.com/kubesphere/kubesphere/issues/3105)
- 修复多集群下流水线触发的问题 [#2626](https://kubesphere.com.cn/forum/d/2626-webhook-jenkins)
- 修复某些情况下编辑流水线时导致的数据丢失问题 [#1270](https://github.com/kubesphere/console/issues/1270)
- 修复点击 "Docker Container Registry Credentials"时的报错问题 [#1269](https://github.com/kubesphere/console/issues/1269)
- 修复英文控制台显示中文代码质量检查结果的问题 [#1278](https://github.com/kubesphere/console/issues/1278)
- 修复 Jenkinsfile 中包含布尔值时的显示报错问题 [#3043](https://github.com/kubesphere/kubesphere/issues/3043)