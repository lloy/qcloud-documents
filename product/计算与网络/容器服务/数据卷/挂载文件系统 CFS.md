## 前提条件
如果您还未创建文件系统，您需要先创建文件系统。有关如何创建文件系统的详细信息，参见 [创建文件系统及挂载点](https://www.qcloud.com/document/product/582/9132) 。

## 查看CFS
1. 登录 [文件系统 CFS 控制台](https://console.qcloud.com/cfs)。
2. 查看 CFS 的可用区，本文档以北京一区为例。单击 **ID/名称**。
![](//mc.qcloudimg.com/static/img/75f0d7b6f4599883e2aac066e1dce03a/image.png)
3. 单击 **挂载点信息** 。
 - **网络信息**：docker-test 和 docker。
 - **挂载路径**： 10.0.0.7:/ 。
 ![](//mc.qcloudimg.com/static/img/568bdbf08e779c9b1dce47d6b6fb719a/image.png)
 
## 创建集群 
容器可以挂载的 CFS（文件系统）需与集群在同一个 vpc 网络同一子网内，因此在创建集群时需要设置在同一个 vpc 网络同一子网内。
有关如何创建集群的详细信息，参见 [新建集群](https://cloud.tencent.com/document/product/457/9091) 。
- **可用区**：选择与 CFS 相同的可用区。此处选择北京一区。
- **节点网络**：选择与 CFS 相同的网络信息。此处选择 docker-test，docker。
- **容器网络**：选择与 CFS 同一个网段内。
![](//mc.qcloudimg.com/static/img/f0a3e622d4fc71b354bb44e7faf38e73/image.png)

## 创建服务
有关如何创建集群的详细信息，参见 [服务的基本操作](https://www.qcloud.com/document/product/457/9096)。
1. 添加数据卷。
 - **类型**：选择 NFS 盘。
 - **名称**：数据卷的名称。此处以 cfs 为例。
 - **路径**：填写 CFS 的挂载路径：10.0.0.7:/。
![](//mc.qcloudimg.com/static/img/a514e6fcb76a07182ced69ddfcd68df1/image.png)

2. 设置挂载点。
单击运行容器下的 **显示高级设置**。
![](//mc.qcloudimg.com/static/img/1e6f5c80d5f78e58fb475d82676f9e88/image.png)

## 更多
若要挂载子目录，需要在挂载前创建好对应的子目录，容器服务挂载 CFS 盘不会自动创建不存在的目录。