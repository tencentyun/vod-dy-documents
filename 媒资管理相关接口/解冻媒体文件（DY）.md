## 1. 接口描述

<strong><font color="red">此接口被设置为 官网公开展示 。</font></strong>

接口请求域名： vod.tencentcloudapi.com 。

当媒体文件的存储类型是归档存储或深度归档存储时，是不可访问的。如需访问，则需要调用本接口进行解冻，解冻后可访问的媒体文件是临时的，在有效期过后，则不可访问。

<div class="rno-api-explorer">
    <div class="rno-api-explorer-inner">
        <div class="rno-api-explorer-hd">
            <div class="rno-api-explorer-title">
                推荐使用 API Explorer
            </div>
            <a href="https://console.cloud.tencent.com/api/explorer?Product=vod&Version=2018-07-17&Action=RestoreMediaForDY" class="rno-api-explorer-btn" hotrep="doc.api.explorerbtn"><i class="rno-icon-explorer"></i>点击调试</a>
        </div>
        <div class="rno-api-explorer-body">
            <div class="rno-api-explorer-cont">
                API Explorer 提供了在线调用、签名验证、SDK 代码生成和快速检索接口等能力。您可查看每次调用的请求内容和返回结果以及自动生成 SDK 调用示例。
            </div>
        </div>
    </div>
</div>

## 2. 输入参数

以下请求参数列表仅列出了接口请求参数和部分公共参数，完整公共参数列表见 [公共请求参数](https://cloud.tencent.com/document/api/213/6976)。

| 参数名称 | 必选 | 类型 | 描述 |
|---------|---------|---------|---------|
| Action | 是 | String | 公共参数，本接口取值：RestoreMediaForDY。 |
| Version | 是 | String | 公共参数，本接口取值：2018-07-17。 |
| Region | 否 | String | 公共参数，本接口不需要传递此参数。 |
| CosBucket | 是 | String | 文件所在的 COS Bucket 名，如 bucket-xxx。 |
| CosRegion | 是 | String | 文件所在的 COS Bucket 所属园区，如 ap-chongqing。 |
| Object | 是 | String | 文件的 COS 完整路径。 |
| RestoreDay | 否 | Integer | 解冻出的临时媒体文件的可访问持续时长，单位为“天”。默认为1天。 |
| SourceContext | 否 | String | 来源上下文，用于透传用户请求信息，最长 1000 个字符。 |

## 3. 输出参数

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| RequestId | String | 唯一请求 ID，每次请求都会返回。定位问题时需要提供该次请求的 RequestId。|

## 4. 示例

### 示例1 解冻媒体文件

#### 输入示例

```
POST / HTTP/1.1
Host: vod.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: RestoreMediaForDY
<公共请求参数>

{
    "SourceContext": "xxxx", 
    "CosBucket": "bucket-xxx", 
    "CosRegion": "ap-chongqing", 
    "Object": "2021/0101/xxx.mp4", 
    "RestoreDay": 1
}
```

#### 输出示例

```
{
  "Response": {
    "RequestId": "requestId"
  }
}
```


## 5. 开发者资源

### 腾讯云 API 平台

[腾讯云 API 平台](https://cloud.tencent.com/api) 是综合 API 文档、错误码、API Explorer 及 SDK 等资源的统一查询平台，方便您从同一入口查询及使用腾讯云提供的所有 API 服务。

### API Inspector

用户可通过 [API Inspector](https://cloud.tencent.com/document/product/1278/49361) 查看控制台每一步操作关联的 API 调用情况，并自动生成各语言版本的 API 代码，也可前往 [API Explorer](https://cloud.tencent.com/document/product/1278/46697) 进行在线调试。

### 命令行工具

* [Tencent Cloud CLI 3.0](https://cloud.tencent.com/document/product/440/6176)

## 6. 错误码

以下仅列出了接口业务逻辑相关的错误码，其他错误码详见 [公共错误码](https://cloud.tencent.com/document/api/213/6982)。

| 错误码 | 描述 |
|---------|---------|
| FailedOperation | 操作失败。 |
| InternalError | 内部错误。 |
| InvalidParameter | 参数错误。 |
| InvalidParameterValue | 参数取值错误。 |
| InvalidParameterValue.NotRestorable | 参数错误：文件不支持解冻。 |
| InvalidParameterValue.RestoreDay | 参数错误：解冻天数错误。 |
| ResourceNotFound | 资源不存在。 |
| ResourceNotFound.FileNotExist | 资源不存在：文件不存在。 |
| ResourceUnavailable | 资源不可用。 |
| UnauthorizedOperation | 未授权操作。 |
| UnknownParameter | 未知参数错误。 |
| UnsupportedOperation | 操作不支持。 |
