## 1. 接口描述

接口请求域名： vod.tencentcloudapi.com 。

对 COS 中的媒体文件发起处理任务，功能包括：
1. 视频转码（带水印）；
2. 视频转动图；
3. 对视频按指定时间点截图；
4. 对视频采样截图；
5. 对视频截图雪碧图；
6. 对视频转自适应码流；
7. 智能内容审核（鉴黄、鉴恐、鉴政）；
8. 智能内容分析（标签、分类、封面、按帧标签）；
9. 智能内容识别（人脸、文本全文、文本关键词、语音全文、语音关键词）。

<div class="rno-api-explorer">
    <div class="rno-api-explorer-inner">
        <div class="rno-api-explorer-hd">
            <div class="rno-api-explorer-title">
                推荐使用 API Explorer
            </div>
            <a href="https://console.cloud.tencent.com/api/explorer?Product=vod&Version=2018-07-17&Action=ProcessMediaForDY" class="rno-api-explorer-btn" hotrep="doc.api.explorerbtn"><i class="rno-icon-explorer"></i>点击调试</a>
        </div>
        <div class="rno-api-explorer-body">
            <div class="rno-api-explorer-cont">
                API Explorer 提供了在线调用、签名验证、SDK 代码生成和快速检索接口等能力。您可查看每次调用的请求内容和返回结果以及自动生成 SDK 调用示例。
            </div>
        </div>
    </div>
</div>

## 2. 输入参数

以下请求参数列表仅列出了接口请求参数和部分公共参数，完整公共参数列表见 [公共请求参数](https://cloud.tencent.com/document/api/266/31756)。

| 参数名称 | 必选 | 类型 | 描述 |
|---------|---------|---------|---------|
| Action | 是 | String | [公共参数](https://cloud.tencent.com/document/api/266/31756)，本接口取值：ProcessMediaForDY。 |
| Version | 是 | String | [公共参数](https://cloud.tencent.com/document/api/266/31756)，本接口取值：2018-07-17。 |
| Region | 否 | String | [公共参数](https://cloud.tencent.com/document/api/266/31756)，本接口不需要传递此参数。 |
| InputInfo | 是 | [MediaInputInfoForDY](../数据结构.md#MediaInputInfoForDY) | 视频处理的文件输入信息。 |
| OutputStorage | 否 | [TaskOutputStorageForDY](../数据结构.md#TaskOutputStorageForDY) | 视频处理输出文件的目标存储。<br/>当 InputInfo 的输入类型是 COS 时可以不填，不填代表继承 InputInfo 中的存储位置。 |
| OutputDir | 否 | String | 视频处理生成的文件输出的目标目录，如`/movie/201907/`。如果不填，表示与 InputInfo 中文件所在的目录一致。<br/>示例值：/movie/201907/ |
| MediaProcessTask | 否 | [MediaProcessTaskInputForDY](../数据结构.md#MediaProcessTaskInputForDY) | 视频处理类型任务参数。 |
| TasksPriority | 否 | Integer | 任务流的优先级，数值越大优先级越高，取值范围是-10到 10，不填代表0。<br/>示例值：0 |
| SessionId | 否 | String | 用于去重的识别码，如果三天内曾有过相同的识别码的请求，则本次的请求会返回错误。最长 50 个字符，不带或者带空字符串表示不做去重。<br/>示例值：123 |
| SessionContext | 否 | String | 来源上下文，用于透传用户请求信息，任务流状态变更回调将返回该字段值，最长 1000 个字符。<br/>示例值：123 |

## 3. 输出参数

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| TaskId | String | 任务 ID。<br/>示例值：125xxx65-procedurev2-bffb15f07530b57bc1aabb01fac74bca|
| RequestId | String | 唯一请求 ID，由服务端生成，每次请求都会返回（若请求因其他原因未能抵达服务端，则该次请求不会获得 RequestId）。定位问题时需要提供该次请求的 RequestId。|

## 4. 示例

### 示例1 发起转码任务

对指定 COS 地址的视频发起转码任务，转出20，30，40三种格式。

#### 输入示例

```
POST / HTTP/1.1
Host: vod.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: ProcessMediaForDY
<公共请求参数>

{
    "InputInfo": {
        "Type": "COS",
        "CosInputInfo": {
            "Bucket": "TopRankVideo-125xxx88",
            "Region": "ap-chongqing",
            "Object": "/movie/201907/WildAnimal.mov"
        }
    },
    "MediaProcessTask": {
        "TranscodeTaskSet": [
            {
                "Definition": 20
            },
            {
                "Definition": 30
            },
            {
                "Definition": 40
            }
        ]
    }
}
```

#### 输出示例

```json
{
    "Response": {
        "RequestId": "6ca31e3a-6b8e-4b4e-9256-fdc700064ef3",
        "TaskId": "125xxx65-procedurev2-bffb15f07530b57bc1aabb01fac74bca"
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

以下仅列出了接口业务逻辑相关的错误码，其他错误码详见 [公共错误码](https://cloud.tencent.com/document/api/266/31774#.E5.85.AC.E5.85.B1.E9.94.99.E8.AF.AF.E7.A0.81)。

| 错误码 | 描述 |
|---------|---------|
| InternalError | 内部错误。 |
| InvalidParameter | 参数错误。 |
| InvalidParameterValue.SessionContextTooLong | SessionContext 过长。 |
| InvalidParameterValue.SessionId | 去重识别码重复，请求被去重。 |
| InvalidParameterValue.SessionIdTooLong | SessionId 过长。 |
