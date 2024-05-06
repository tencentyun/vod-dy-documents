## 1. 接口描述

接口请求域名： vod.tencentcloudapi.com 。

通过任务 ID 查询任务的执行状态和结果的详细信息（最多可以查询3天之内提交的任务）。

<div class="rno-api-explorer">
    <div class="rno-api-explorer-inner">
        <div class="rno-api-explorer-hd">
            <div class="rno-api-explorer-title">
                推荐使用 API Explorer
            </div>
            <a href="https://console.cloud.tencent.com/api/explorer?Product=vod&Version=2018-07-17&Action=DescribeTaskDetailForDY" class="rno-api-explorer-btn" hotrep="doc.api.explorerbtn"><i class="rno-icon-explorer"></i>点击调试</a>
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
| Action | 是 | String | [公共参数](https://cloud.tencent.com/document/api/266/31756)，本接口取值：DescribeTaskDetailForDY。 |
| Version | 是 | String | [公共参数](https://cloud.tencent.com/document/api/266/31756)，本接口取值：2018-07-17。 |
| Region | 否 | String | [公共参数](https://cloud.tencent.com/document/api/266/31756)，本接口不需要传递此参数。 |
| TaskId | 是 | String | 视频处理任务的任务 ID。<br/>示例值：235303****-WorkflowTask-80108cc3380155d98b2e3573a48a****** |

## 3. 输出参数

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| TaskType | String | 任务类型，目前取值有：<br/><li>WorkflowTask：视频工作流处理任务。</li><li>EditMediaTask：视频编辑任务。</li><li>LiveStreamProcessTask：直播流处理任务。</li><br/>示例值：WorkflowTask|
| Status | String | 任务状态，取值：<br/><li>WAITING：等待中；</li><li>PROCESSING：处理中；</li><li>FINISH：已完成。</li><br/>示例值：FINISH|
| CreateTime | String | 任务的创建时间，采用 [ISO 日期格式](https://cloud.tencent.com/document/product/266/11732#I)。<br/>示例值：2019-07-16T06:21:27Z|
| BeginProcessTime | String | 任务开始执行的时间，采用 [ISO 日期格式](https://cloud.tencent.com/document/product/266/11732#I)。<br/>示例值：2019-07-16T06:21:28Z|
| FinishTime | String | 任务执行完毕的时间，采用 [ISO 日期格式](https://cloud.tencent.com/document/product/266/11732#I)。<br/>示例值：2019-07-16T06:21:46Z|
| WorkflowTask | [WorkflowTaskForDY](../数据结构.md#WorkflowTaskForDY) | 视频处理任务信息，仅当 TaskType 为 WorkflowTask，该字段有值。<br/>注意：此字段可能返回 null，表示取不到有效值。|
| EditMediaTask | [EditMediaTaskForDY](../数据结构.md#EditMediaTaskForDY) | 视频编辑任务信息，仅当 TaskType 为 EditMediaTask，该字段有值。<br/>注意：此字段可能返回 null，表示取不到有效值。|
| TasksPriority | Integer | 任务流的优先级，取值范围为 [-10, 10]。<br/>示例值：0|
| SessionId | String | 用于去重的识别码，如果七天内曾有过相同的识别码的请求，则本次的请求会返回错误。最长50个字符，不带或者带空字符串表示不做去重。<br/>示例值：""|
| SessionContext | String | 来源上下文，用于透传用户请求信息，任务流状态变更回调将返回该字段值，最长1000个字符。<br/>示例值：""|
| ExtInfo | String | 扩展信息字段，仅用于特定场景。<br/>示例值：""|
| RequestId | String | 唯一请求 ID，由服务端生成，每次请求都会返回（若请求因其他原因未能抵达服务端，则该次请求不会获得 RequestId）。定位问题时需要提供该次请求的 RequestId。|

## 4. 示例

### 示例1 获取任务详情

#### 输入示例

```
https://vod.tencentcloudapi.com/?Action=DescribeTaskDetailForDY
&TaskId=235303****-WorkflowTask-80108cc3380155d98b2e3573a48a******
&<公共请求参数>
```

#### 输出示例

```json
{
    "Response": {
        "TaskType": "WorkflowTask",
        "Status": "FINISH",
        "CreateTime": "2019-07-16T06:21:27Z",
        "BeginProcessTime": "2019-07-16T06:21:28Z",
        "FinishTime": "2019-07-16T06:21:46Z",
        "EditMediaTask": null,
        "WorkflowTask": null,
        "TasksPriority": 0,
        "SessionId": "",
        "SessionContext": "",
        "ExtInfo": "",
        "RequestId": "04db7d25-f590-414a-a341-8f1584f15f84"
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
| FailedOperation.InvalidVodUser | 没有开通点播业务。 |
| InternalError | 内部错误。 |
| InvalidParameterValue | 参数取值错误。 |
| ResourceNotFound | 资源不存在。 |
| UnauthorizedOperation | 未授权操作。 |
