### 一、通用首部

### 二、请求首部
#### Accept
Accept 首部字段可以通知服务器，用户代理能够处理的媒体类型及优先级顺序。 <br />
例子：Accept：text/html, text/plain

#### Accept-Charset
Accept-Charset 首部字段可以用来通知服务器，用户代理支持的字符集及优先级顺序。 <br />
例子：Accept-Charset: iso-8859-5, unicode-1-1; q=0.8

#### Accept-Encoding
Accept-Encoding 首部字段用来告知服务器，用户代理支持的内容编码及优先级顺序。 <br />
例子：Accept-Encoding：gzip, deflate

#### Accept-Language
Accept-Language 首部字段用来告知服务器，用户代理能够处理的自然语言集及优先级顺序。 <br />
例子：Accept-Language：zh-cn,zh; q=0.7, en-us,en; q=0.3

#### Authorization
Authorization 首部字段用来告知服务器，用户代理的认证信息。 <br />
例子: Authorization: Basic dWVub3NlbjpwYXNzd29yZA==

#### Except
Except 首部字段用来告知服务器，期望出现的某种特定行为。因服务器无法理解客户端的期望做出回应而发生错误时，会返回状态码 417 Expectation Failed。 <br />
例子：Except：100-continue

#### Form
Form 首部字段用来告知服务器，使用用户代理的用户的电子邮件地址。 <br />
例子：Form：123456@qq.com

#### Host
Host 首部字段用来告知服务器，请求的资源所处的互联网主机名和端口号。 <br />
例子：Host：www.baidu.com

#### If-Match
If-Match 首部字段属附带条件之一，它会告知服务器匹配资源所用的实体标记(ETag)值，这时服务器无法使用弱 ETag 值。<br />
服务器会对比 If-Match 的字段值和资源的 ETag 值，仅当两者一致时，才会执行请求。反之服务器返回 412 Precondition Failed 的响应。 <br />
还可以使用星号（*）指定 If-Match 的字段值。针对这种情况，服务
器将会忽略 ETag 的值，只要资源存在就处理请求。
 <br />
例子：If-Match："123456"

### 三、响应首部

### 四、实体首部