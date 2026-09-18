# ServiceMind｜私人源码学习档案

这是本人购买的多 Agent 客服项目的**私有备份与复现资料入口**。ServiceMind 是个人展示名称，原始工程仍保留 EchoMind 的内部命名和来源标记，不通过改名宣称原创，也不授予第三方再分发权。

公开架构说明：[ServiceMind 学习展示](https://github.com/jiangenjing/servicemind-agent-demo)。

## 内容

- [源码压缩包](source-bundle-private.zip)：Python 后端、Java 后端、Vue 前端、配置、测试、业务 Skills。
- [逐文件校验清单](MANIFEST.json)：相对路径、大小与 SHA-256。
- [安全配置样例](backend.env.example)：需自己填写模型和本地凭据，不含真实 Key。

为减少未经授权传播的风险，付费讲义、简历包装模板没有上传。也排除了 `.env`、数据库、聊天记录、日志、Git 历史、虚拟环境、依赖目录、编译产物和 IDE 配置；源文件中的邮箱与个人绝对路径做了脱敏。原始资料没有被修改。

## 解压后的结构

```text
EchoMind/          Python / FastAPI 后端，建议先学习这一版
EchoMindJava/      Java / Spring Boot 对照实现
EchoMindFrontend/  Vue 3 / Vite 调试前端
```

保留三个目录的相对关系，因为前端 Compose 的 build context 会引用另两个目录。不要为换展示名而盲目替换服务标识和包名。

## 复现起点

1. 解压到新的学习目录，不覆盖正在使用的工程。
2. 阅读公开架构说明，先确定 Python 请求主链路。
3. 将安全配置样例复制为 Python 目录的 `.env`，填写合法可用的模型、Key 和 Redis 密码。
4. 在 Python 目录执行 `docker compose config --quiet`，然后按需构建启动。默认配置会暴露本地端口，未加鉴权前不要发布公网服务。
5. Vue 目录执行 `npm ci`、`npm run dev`，连接本地 Python API。
6. 先验证健康、知识导入与独立检索，再做对话、工具 Trace 和评测。评测可能产生 API 费用。

## 当前验证边界

本次整理进行了静态代码核查、打包路径检查和凭据模式筛查。没有使用真实密钥调用模型，没有启动新的公网客服服务，没有证明 Java/Python 两版功能等价。后续实测应保存测试输入、模型版本、预期输出、实际结果和错误记录。

源码中的默认密码只是演示配置，不能在对外部署中使用。正则检查也不能覆盖所有潜在敏感信息；只有确认授权和进一步安全审计后，才考虑公开任何源码。
