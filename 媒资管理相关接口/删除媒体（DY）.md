## 1. 接口描述

<strong><font color="blue">此接口被设置为 产品内部展示 。</font></strong>

接口请求域名： vod.tencentcloudapi.com 。

删除指定文件，如果是 m3u8 文件，会同时删除 ts 文件。

<div class="rno-api-explorer">
    <div class="rno-api-explorer-inner">
        <div class="rno-api-explorer-hd">
            <div class="rno-api-explorer-title">
                推荐使用 API Explorer
            </div>
            <a href="https://console.cloud.tencent.com/api/explorer?Product=vod&Version=2018-07-17&Action=DeleteMediaForDY" class="rno-api-explorer-btn" hotrep="doc.api.explorerbtn"><i class="rno-icon-explorer"></i>点击调试</a>
        </div>
        <div class="rno-api-explorer-body">
            <div class="rno-api-explorer-cont">
                API Explorer 提供了在线调用、签名验证、SDK 代码生成和快速检索接口等能力。您可查看每次调用的请求内容和返回结果以及自动生成 SDK 调用示例。
            </div>
        </div>
    </div>
</div>

## 2. 输入参数

以下请求参数列表仅列出了接口请求参数和部分公共参数，完整公共参数列表见 [公共请求参数](https://cloud.tencent.com/document/product/266/17841?!preview&preview_docmenu=1&lang=cn&!document=1)。

| 参数名称 | 必选 | 类型 | 描述 |
|---------|---------|---------|---------|
| Action | 是 | String | 公共参数，本接口取值：DeleteMediaForDY。 |
| Version | 是 | String | 公共参数，本接口取值：2018-07-17。 |
| Region | 否 | String | 公共参数，本接口不需要传递此参数。 |
| CosBucket | 是 | String | 文件所在的 COS Bucket 名，如 wsd-tx-ugc-pub。 |
| CosRegion | 是 | String | 文件所在的 COS Bucket 所属园区，如 ap-chongqing。 |
| ObjectSet.N | 是 | Array of String | 文件的 COS 完整路径。 |

## 3. 输出参数

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| RequestId | String | 唯一请求 ID，每次请求都会返回。定位问题时需要提供该次请求的 RequestId。|

## 4. 示例

### 示例1 删除媒体文件

#### 输入示例

```
https://vod.tencentcloudapi.com/?Action=DeleteMediaForDY
&CosBucket=wsd-tx-ugc-pub
&CosRegion=ap-chongqing
&ObjectSet.0=2021/0101/xxx.m3u8
&<公共请求参数>
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

以下仅列出了接口业务逻辑相关的错误码，其他错误码详见 [公共错误码](https://cloud.tencent.com/document/product/266/17843?!preview&preview_docmenu=1&lang=cn&!document=1#.E5.85.AC.E5.85.B1.E9.94.99.E8.AF.AF.E7.A0.81)。

| 错误码 | 描述 |
|---------|---------|
| FailedOperation | 操作失败。 |
| FailedOperation.InvalidVodUser | 没有开通点播业务。 |
| InternalError | 内部错误。 |
| InvalidParameterValue | 参数取值错误。 |
| ResourceNotFound | 资源不存在。 |
| UnauthorizedOperation | 未授权操作。 |
