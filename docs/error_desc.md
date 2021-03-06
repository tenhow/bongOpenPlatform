###错误响应说明

开放平台OAuth2.0在接受验证授权请求时，授权服务器会按照OAuth2.0协议对本次请求参数、请求头部进行校验，若请求不合法或验证未通过，授权服务器会返回相应的错误信息。

####特别说明
在接口调用过程中，如遇返回400和401错误码，应重新请求对应用户的访问权限，即再次请求request_token与access_token。上线应用需要具备遇到该情况时重新获取 access_token 的功能。

#####错误码简介
错误码主要分为两种方式:
*  在授权获取过程中或者接口调用过程中与权限相关的错误。
*  在接口调用过程中返回的相关错误。


#####授权错误码说明

错误码|错误信息|详细描述
|---|---|---|
invalid_request|invalid refresh token|请求缺少某个必需参数，或者格式不正确。
invalid_client|unknown client id|client_id”、“client_secret”参数无效。
invalid_grant|The provided authorization grant is revoked|提供的Access Grant是无效的、过期的或已撤销。
unauthorized_client|The client is not authorized to use this authorization grant type|应用没有被授权。
unsupported_grant_type|The authorization grant type is not supported|不支持该参数。
invalid_scope|The requested scope is exceeds the scope granted by the resource owner|请求的“scope”参数是无效的。
expired_token|refresh token has been used|Refresh Token已过期。
redirect_uri_mismatch|Invalid redirect uri|“redirect_uri”不匹配。

#####接口错误码说明
返回值|说明
---|---
401|未授权
402|请求参数错误
403|签名错误
405|查询用户与认证用户不符
500|服务器内部错误
2001|未知错误(请与管理员联系)
2002|请求人数已达上限
2003|请求人数已达下限
2004|用户已在event中
2005|用户不在event中
2006|不存在的event
2007|超过日期数量上限
2008|内容长度超过限制
2012|未绑定