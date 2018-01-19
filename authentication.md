# 认证

## 认证方式

XiXisys 使用 access_token 来授权每一个 API 请求，你可以通过 POST 请求 /oauth/token 的方式来获取 access_token，该 token 在 expires_in 的时间里都是有效的，所以可以将该 token 之存在缓存里，方便在每一次请求中使用

## 请求说明

```
http请求方式: POST
https://open.xixisys.com/oauth/token
```

## 示例

```php
$guzzle = new GuzzleHttp\Client;
$response = $guzzle->post('https://open.xixisys.com/oauth/token', [
    'form_params' => [
        'grant_type' => 'client_credentials',
        'client_id' => 'CLIENT_ID',
        'client_secret' => 'CLIENT_SECRET', 
    ],
]);
echo json_decode((string) $response->getBody(), true);
```

## 参数说明

|参数|是否必须|说明|
|----|-------|----|
|grant_type|是|填写`client_credentials`|
|client_id|是|填写客户端的授权ID|
|client_secret|是|填写客户端的授权秘钥|

## 返回结果

```json
{
  "token_type": "Bearer",
  "expires_in": 31536000, // 秒
  "access_token": "...",
}
```

## 结果说明

返回结果得到的数据可以用于每一次 API 请求，认证的请求头部都应该包含如下的 Header

`Authorization: {token_type} {access_token} // token_type 和 access_token 是 API 返回的`
