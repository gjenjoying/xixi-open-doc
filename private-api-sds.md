# 获取私有 SDS

## 请求说明

```
http请求方式: GET
https://open.xixisys.com/api/private/sds/{cas}/{edition?}
```

## 示例

```php
$guzzle = new GuzzleHttp\Client;
// 获取中文版使用 https://open.xixisys.com/api/private/sds/50-00-0/cn
$response = $guzzle->get('https://open.xixisys.com/api/private/sds/50-00-0');
echo json_decode((string) $response->getBody(), true);
```

## 参数说明

|参数|是否必须|说明|
|----|-------|----|
|cas|是|SDS 对应的 CAS 号|
|edition|否|默认`ghs`(`ghs`对应GHS联合国版本，`cn`对应中文版本)|

## 返回结果

```json
{
    html_url: '...',
    pdf_url: '...'
}
```

## 结果说明

|字段|说明|
|----|----|
|html_url|SDS 的 html 地址，过期时间对应 url 中的 e 参数(以秒为单位的时间戳)|
|pdf_url|SDS 的 PDF 地址，可访问之后下载该 pdf 文档|