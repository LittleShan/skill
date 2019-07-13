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

#### If-Modified-Since
If-Modified-Since 首部字段属附带条件之一，它会告知服务器若If-Modified-Since 字段值早于资源更新时间，则希望能处理请求。<br />
否则，返回状态码304 Not Modified 的响应。<br />
例子：If-Modified-Since：Thu，15 Apr 2004 00:00:00 GMT

#### If-None-Match
与 If-Match 作用相反 <br />
在 GET 和或者 HEAD 方法中使用首部字段 If-None-Match 可获取最新资源

#### If-Range
If-Range 首部字段属附带条件之一，它会告知服务器若If-Range 字段值和请求资源的 ETag 值或时间相一致时，则作为范围请求处理。反之，返回全体资源<br />

#### If-Unmodified-Since
与 If-Modified-Since 作用相反 <br />
如果在指定的日期之后，资源发生了更新则返回 412 

#### Max-Forwards
可经过的服务器最大树木 <br />
例子：Max-Forwards：10

#### Proxy-Authorization
接收到从代理服务器发来的认证质询时，客户端会发送包含首部字段Proxy-Authorization的请求，以告知服务器所需要的认证信息。 <br />
认证行为发生在客户端与代理服务器之间。客户端与服务器之间的认证使用 Authorization。

#### Range
获取部分资源的范围请求，接收到Range首部字段请求的服务器，会在处理请求之后返回状态码为 206 Partial Content 的响应。无法处理范围请求时，则会返回200的响应及全部资源。<br />
例子：Range：bytes=5001-10000

#### Referer
告知服务器请求的原始资源的URI

#### TE
首部字段TE会告知服务器客户端能够处理的响应的传输编码方式及相对优先级。<br />
TE 除了可以指定传输编码之外，还可以指定伴随trailer字段的分块传输编码的方式，应用后者时，只需要把trailer赋值给该字段<br >
例子：TE：gzip, deflate;q=0.5 <br />
例子：TE：trailer

#### User-Agent
User-Agent 会将创建请求的浏览器和用户代理名称传递给服务器

### 三、响应首部

### 四、实体首部