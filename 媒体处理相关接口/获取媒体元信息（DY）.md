## 1. 接口描述

接口请求域名： vod.tencentcloudapi.com 。

获取媒体的元信息，包括视频画面宽、高、编码格式、时长、帧率等。

<div class="rno-api-explorer">
    <div class="rno-api-explorer-inner">
        <div class="rno-api-explorer-hd">
            <div class="rno-api-explorer-title">
                推荐使用 API Explorer
            </div>
            <a href="https://console.cloud.tencent.com/api/explorer?Product=vod&Version=2018-07-17&Action=DescribeMediaMetaDataForDY" class="rno-api-explorer-btn" hotrep="doc.api.explorerbtn"><i class="rno-icon-explorer"></i>点击调试</a>
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
| Action | 是 | String | [公共参数](https://cloud.tencent.com/document/api/266/31756)，本接口取值：DescribeMediaMetaDataForDY。 |
| Version | 是 | String | [公共参数](https://cloud.tencent.com/document/api/266/31756)，本接口取值：2018-07-17。 |
| Region | 否 | String | [公共参数](https://cloud.tencent.com/document/api/266/31756)，本接口不需要传递此参数。 |
| InputInfo | 是 | [MediaInputInfoForDY](../数据结构.md#MediaInputInfoForDY) | 需要获取元信息的文件输入信息。 |

## 3. 输出参数

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| MetaData | [MediaMetaDataForDY](../数据结构.md#MediaMetaDataForDY) | 媒体元信息。|
| RequestId | String | 唯一请求 ID，由服务端生成，每次请求都会返回（若请求因其他原因未能抵达服务端，则该次请求不会获得 RequestId）。定位问题时需要提供该次请求的 RequestId。|

## 4. 示例

### 示例1 获取视频信息

#### 输入示例

```
https://vod.tencentcloudapi.com/?Action=DescribeMediaMetaDataForDY
&InputInfo.Type=COS
&InputInfo.CosInputInfo.Bucket=TopRankVideo-125xxx88
&InputInfo.CosInputInfo.Region=ap-chongqing
&InputInfo.CosInputInfo.Object=/movie/201907/WildAnimal.mov
&<公共请求参数>
```

#### 输出示例

```json
{
    "Response": {
        "MetaData": {
            "AudioDuration": 380.9465637207031,
            "AudioStreamSet": [
                {
                    "Bitrate": 95999,
                    "Codec": "aac",
                    "SamplingRate": 44100
                }
            ],
            "Bitrate": 409657,
            "Container": "mov,mp4,m4a,3gp,3g2,mj2",
            "Duration": 380.9465637207031,
            "Height": 360,
            "Rotate": 0,
            "Size": 19626862,
            "VideoDuration": 380.8804931640625,
            "VideoStreamSet": [
                {
                    "Bitrate": 313658,
                    "Codec": "h264",
                    "Fps": 29,
                    "Height": 360,
                    "Width": 480
                }
            ],
            "Width": 480
        },
        "RequestId": "12ae8d8e-dce3-4151-9d4b-5594145287e1"
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
| InvalidParameter | 参数错误。 |
| InvalidParameterValue.SrcFile | 源文件错误。 |
