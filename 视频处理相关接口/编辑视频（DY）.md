## 1. 接口描述

<strong><font color="blue">此接口被设置为 产品内部展示 。</font></strong>

接口请求域名： vod.tencentcloudapi.com 。

对视频进行编辑（剪辑、拼接等），生成一个新的点播视频。编辑的功能包括：

1. 对一个文件进行剪辑，生成一个新的视频；
2. 对多个文件进行拼接，生成一个新的视频；
3. 对多个文件进行剪辑，然后再拼接，生成一个新的视频。

<div class="rno-api-explorer">
    <div class="rno-api-explorer-inner">
        <div class="rno-api-explorer-hd">
            <div class="rno-api-explorer-title">
                推荐使用 API Explorer
            </div>
            <a href="https://console.cloud.tencent.com/api/explorer?Product=vod&Version=2018-07-17&Action=EditMediaForDY" class="rno-api-explorer-btn" hotrep="doc.api.explorerbtn"><i class="rno-icon-explorer"></i>点击调试</a>
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
| Action | 是 | String | 公共参数，本接口取值：EditMediaForDY。 |
| Version | 是 | String | 公共参数，本接口取值：2018-07-17。 |
| Region | 否 | String | 公共参数，本接口不需要传递此参数。 |
| FileInfos.N | 是 | Array of [EditMediaFileInfoForDY](../数据结构.md#EditMediaFileInfoForDY) | 输入的视频文件信息。 |
| OutputStorage | 是 | [TaskOutputStorageForDY](../数据结构.md#TaskOutputStorageForDY) | 视频处理输出文件的目标存储。 |
| OutputObjectPath | 是 | String | 视频处理输出文件的目标路径。 |
| OutputConfig | 否 | [EditMediaOutputConfigForDY](../数据结构.md#EditMediaOutputConfigForDY) | 编辑后生成的文件配置。 |
| TasksPriority | 否 | Integer | 任务优先级，数值越大优先级越高，取值范围是-10到 10，不填代表0。 |
| SessionId | 否 | String | 用于去重的识别码，如果三天内曾有过相同的识别码的请求，则本次的请求会返回错误。最长 50 个字符，不带或者带空字符串表示不做去重。 |
| SessionContext | 否 | String | 来源上下文，用于透传用户请求信息，任务流状态变更回调将返回该字段值，最长 1000 个字符。 |

## 3. 输出参数

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| TaskId | String | 编辑视频的任务 ID，可以通过该 ID 查询编辑任务的状态。|
| RequestId | String | 唯一请求 ID，每次请求都会返回。定位问题时需要提供该次请求的 RequestId。|

## 4. 示例

### 示例1 对一个文件进行剪辑，生成一个新的视频

#### 输入示例

```
https://vod.tencentcloudapi.com/?Action=EditMediaForDY
&FileInfos.0.InputInfo.Type=COS
&FileInfos.0.InputInfo.CosInputInfo.Bucket=TopRankVideo-125xxx88
&FileInfos.0.InputInfo.CosInputInfo.Region=ap-chongqing
&FileInfos.0.InputInfo.CosInputInfo.Object=/movie/201907/WildAnimal.mov
&FileInfos.0.StartTimeOffset=60.0
&FileInfos.0.EndTimeOffset=120.0
&OutputStorage.Type=COS
&OutputStorage.CosOutputStorage.Bucket=TopRankVideo-125xxx88
&OutputStorage.CosOutputStorage.Region=ap-chongqing
&OutputObjectPath=/clip_result/clip_WildAnimal.{format}
&<公共请求参数>
```

#### 输出示例

```
{
  "Response": {
    "RequestId": "6ca31e3a-6b8e-4b4e-9256-fdc700064ef3",
    "TaskId": "125xxx88-EditMedia-bffb15f07530b57bc1aabb01fac74bca"
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
| InternalError | 内部错误。 |
| InvalidParameter | 参数错误。 |
