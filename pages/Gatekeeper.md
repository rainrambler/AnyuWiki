- Gatekeeper 子系统会在可信执行环境 (TEE) 中执行设备解锁图案/密码身份验证。Gatekeeper 会使用由硬件支持的密钥通过 HMAC 注册和验证密码。此外，Gatekeeper 会限制连续失败的验证尝试次数，并且必须根据指定的超时和指定的连续失败尝试次数拒绝服务请求。
- 当用户验证其密码时，Gatekeeper 会使用 TEE 派生的共享密钥对身份验证认证签名，以发送至由硬件支持的密钥库。也就是说，Gatekeeper 认证可让 [[Keystore]] 知道可以发布与身份验证绑定的密钥（例如，应用创建的密钥）供应用使用了。
-
- [[macOS]]也支持使用Gatekeeper限制只有来自于可信来源的代码才能在系统中执行。该技术实际上是对 [[spctl]] 命令行的封装。
-