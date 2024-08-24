# Mlchain Premium

Mlchain Premium 是一款 [AWS AMI](https://docs.aws.amazon.com/zh\_cn/AWSEC2/latest/UserGuide/ec2-instances-and-amis.html) 产品，允许自定义品牌，并可作为 EC2 一键部署到你的 AWS VPC 上。前往 [AWS Marketplace](https://aws.amazon.com/marketplace/pp/prodview-t22mebxzwjhu6) 进行订阅并使用，它适合以下场景：

* 在中小型企业内，需在服务器上创建一个或多应用程序，并且关心数据私有化。
* 你对 [Mlchain Cloud ](https://docs.mlchain.khulnasoft.com/v/zh-hans/getting-started/cloud)订阅计划感兴趣，但所需的用例资源超出了[计划](https://mlchain.khulnasoft.com/pricing)内所提供的资源。
* 你希望在组织内采用 Mlchain Enterprise 之前进行 POC 验证。

### 设置

如果这是您第一次访问 Mlchain，请输入管理员初始化密码（设置为你的 EC2 实例 ID）以开始设置过程。

部署 AMI 后，通过 EC2 控制台中找到的实例公有 IP 访问 Mlchain（默认使用 HTTP 端口 80）。

### 升级

在 EC2 实例中，运行以下命令：

```bash
git clone https://github.com/mlchain/mlchain.git /tmp/mlchain
mv -f /tmp/mlchain/docker/* /mlchain/
rm -rf /tmp/mlchain
docker-compose down
docker-compose pull
docker-compose -f docker-compose.yaml -f docker-compose.override.yaml up -d
```

### 定制化

就像自托管部署一样，你可以根据需要修改 EC2 实例中 `.env` 下的环境变量。然后使用以下命令重新启动 Mlchain：

```
docker-compose down
ocker-compose -f docker-compose.yaml -f docker-compose.override.yaml up -d
```
