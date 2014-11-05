#松鼠相册API http://api.songshuyun.com

###手机号注册帐号

1.用户获取手机验证码

    POST /mobile/authorization
**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
|  pnumber | string | **required.** 用户手机号码 |  

2.用户根据手机验证码进行验证

    PUT /mobile/authorization
**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
| pnumber | string | **required.** 用户手机号码 |  
| vcode | string | **required.** 短信验证码 |  

3.mobile user register fns account.

    POST accounts/mobile/
**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
| pnumber | string | **required.** 用户手机号码 |  
| vcode | string | **required.** 短信验证码 |  
| passwd | string | **required.** 帐号密码 |  

### 用户信息
4.用户登录
> Header: Authorization

    GET /user

5.修改用户信息
> Header: Authorization

    PUT /user
**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
| nickname | string | 用户昵称 |  
| avatar | file | 用户头像 |  

6.用户帐号绑定baidu推送channel
> Header: Authorization

    POST /baidu/push
**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
| user_id | string | **required.** 百度推送应用端'user_id'字段 |  
| channel_id | string | **required.** 百度推送应用端'channel_id'字段 |  
| pkg | string | **required** 应用包名 |  

### 用户绑定设备
7.用户申请绑定设备
> HEADER: Authorization

    POST /user/device
**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
| sn | string | **required.** 设备序列号 |  
| rid | int | 角色id |  

### 用户联系人
8.用户添加联系人
> HEADER: Authorization

    POST /user/:username/contact/:contact

**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
| username | string | **required.** 申请人/设备用户名 |  
| contact | string | **required.** 联系人用户名 |  

9.用户获取联系人列表
> HEADER: Authorization

    GET /user/:username/contact

**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
| username | string | **required.** 申请人/设备用户名 |  

10.用户删除联系人
> HEADER: Authorization

    DELETE /user/:username/contact/:contact

**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
| username | string | **required.** 申请人/设备用户名 |  
| contact | string | **required.** 联系人用户名 |  

###相册
12.用户创建相册
> HEADER: Authorization

    POST /circle

**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
| cname | string | **required.** 相册名字 |  

13.获取用户已加入的相册列表
> HEADER: Authorization

    GET /circle

**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
| username | string | 用户名 |  

###相册成员
14.相册添加成员
> HEADER: Authorization

    POST /circle/:slug/user/:username

**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
| slug | string | **required.** 相册slug |  
| username | string | **required.** 用户名 |  

15.相册成员列表
>HEADER: Authorization

    GET /circle/:slug/user

**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
| slug | string | **required.** 相册slug |  

16.相册管理员更新相册成员的角色
>HEADER: Authorization

    PUT /circle/:slug/user/:username

**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
| slug | string | **required.** 相册slug |  
| username | string | **required.** 用户名 |  
| type | string | **required.** 相册角色id |  

17.相册管理员删除成员
> HEADER: Authorization

    DELETE /circle/:slug/user/:username

**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
| slug | string | **required.** 相册slug |  
| username | string | **required.** 用户名 |  

### 相册成员moment列表
18.获取相册成员moment列表
> HEADER: Authorization

    GET /circle/:slug/user/:username/moments

**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
| slug | string | **required.** 相册slug |  
| username | string | **required.** 用户名 |  

### Moment
19.发布moment
> HEADER: Authorization

    POST /moment

**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
| slug | string | **required.** 相册slug |  
| desc | string | moment描述 |  
| photo | file[] | **required.** moment照片文件列表 |  

20.获取moment列表
> HEADER: Authorization

    GET /moment

**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
| slug | string | 相册slug |  
| username | string | 用户名 |  
| page_size | int | 每页显示数量 |  
| page | int | 页码 |  

21.删除moment中的照片
> HEADER: Authorization

    DELETE /moment

**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
| slug | string | **required.** 相册slug |  
| mid | string | **required.** moment中的媒介(照片,音频,视频)id |  

### Moment(v2)
22.获取qiniu上传token.
> HEADER: Authorization

    GET /qiniu/uptoken
23.发布moment
> HEADER: Authorization

    POST /user/moment

**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
| slug | string | 相册slug集合, 多个相册slug以','隔开 |  
| desc | string | moment描述 |  
| photo | string | **required.** moment图片key集合, 多个key以','隔开|  

### 设备
24.设备激活

    POST /device

**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
| sn | string | **required.** 设备序列号 |  
| imei | string | **required.** 设备IMEI号 |  
| mac | string | **required.** 设备MAC地址 |  


### OAuth2
25.验权获取Token.

    POST /oauth2/access_token

**请求参数**

| 参数名 | 类型 | 描述 |  
| ----- | ----------------- | ------------------- |  
| client_id | string | **required.** 客户端id |  
| client_secret | string | **required.** 客户端secret |  
| grant_type | string | **required.** password |  
| username | string | **required.** 用户名 |  
| passwork | string | **required.** 密码 |  
