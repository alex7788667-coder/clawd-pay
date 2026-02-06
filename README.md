# ClawdPay - 企业级聚合支付系统

[![License](https://img.shields.io/badge/license-Apache%202-4EB1BA.svg)](https://www.apache.org/licenses/LICENSE-2.0.html)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![Vue](https://img.shields.io/badge/Vue-3.x-blue.svg)](https://vuejs.org/)

ClawdPay 是一套高性能、高可用的聚合支付中间件系统，旨在为企业提供统一的支付接入能力、商户风控管理及自动化的通道轮询能力。系统支持对接多种上游通道，并内置了轻量级的 H5 交互式收银台。

## 🌟 核心特性

- **聚合支付接入**：统一标准 API，一次接入即可使用多种支付通道（如 Dongwo EasyHome 等）。
- **智能轮询调度**：支持多通道、多子账号（小号）自动轮询，具备额度风控与状态自动切换功能。
- **安全合规**：内置商户 IP 白名单校验、APP_SECRET 验签机制，确保交易链路安全。
- **轻量收银台**：原生 H5 收银台，支持跨平台访问，支持支付链接自动跳转与金额显示。
- **商户管理**：完备的商户体系，支持余额统计、订单对账及异步回调通知。
- **自动化运维**：基于 Docker 的一键部署能力，支持 MyBatis-Plus 高效持久化。

## 🏗️ 系统架构

- **后端 (`payment-system-java`)**: 基于 Java 21 + Spring Boot 3 + MyBatis-Plus + MySQL 构建的核心逻辑层。
- **前端 (`payment-cashier-h5`)**: 极简移动端 H5 收银台，负责呈现支付引导与状态展示。
- **运维组件**: 包含 SQL 自动初始化脚本与 Docker 容器化配置。

## 🚀 快速开始

### 1. 环境准备
- JDK 17+ (推荐 JDK 21)
- MySQL 5.7+ / 8.0
- Docker & Docker Compose (可选)

### 2. 数据库初始化
执行项目根目录下的 `payment-system-java/schema.sql` 脚本，创建 `payment_db` 并初始化基础表结构。

### 3. 后端启动
```bash
cd payment-system-java
# 修改 application.yml 中的数据库配置
mvn clean package
java -jar target/payment-system-java-1.0.0.jar
```

### 4. 前端部署
将 `payment-cashier-h5` 文件夹下的内容部署至 Web 服务器（如 Nginx），并确保生产域名与后端配置中的 `CASHIER_BASE_URL` 保持一致。

## 📖 API 概览

### 统一下单接口
- **URL**: `/api/pay/create`
- **Method**: `POST`
- **Headers**: `Content-Type: application/json`
- **Payload**:
```json
{
  "mch_id": "10001",
  "mch_order_no": "ORD20260206001",
  "amount": "100.00"
}
```
- **Response**: 返回加密后的收银台跳转链接 `pay_url`。

## 🛠️ 技术栈

| 维度 | 技术选型 |
| :--- | :--- |
| 核心框架 | Spring Boot 3.4.1 |
| 持久层 | MyBatis-Plus |
| 数据库 | MySQL 8.0 |
| 前端 | HTML5, JavaScript (Vue 生态兼容) |
| 安全 | IP Whitelist, HMAC Sign |
| 部署 | Docker, Nginx, NIP.IO |

## ⚖️ 开源协议
本项目遵循 Apache License 2.0 开源协议。

## 📩 联系方式
如有任何疑问或合作意向，请联系：
- **Telegram**: [@vip339977](https://t.me/vip339977)

---
**小叶出品，乌巴拉竭诚协助维护。**
