### 请求地址

/api/c/compapi/v2/cc/get_custom_query_data/

### 请求方法

GET

### 功能描述

根据自定义 api 获取数据

### 请求参数

#### 通用参数

| 字段 | 类型 | 必选 | 描述 |
|-----------|------------|--------|------------|
| bk_app_code | string | 是 | 应用  ID |
| bk_app_secret| string | 是 | 安全密钥(应用 TOKEN)，可以通过 蓝鲸智云开发者中心 -&gt; 点击应用 ID -&gt; 基本信息 获取 |
| bk_token | string | 否 | 当前用户登录态，bk_token 与 bk_username 必须一个有效，bk_token 可以通过 Cookie 获取 |
| bk_username | string | 否 | 当前用户用户名，应用免登录态验证白名单中的应用，用此字段指定当前用户 |

#### 接口参数

| 字段 | 类型 | 必选 | 描述 |
|-----------|------------|--------|------------|
| bk_supplier_account | string | 否 | 开发商账号 |
| bk_biz_id | int | 是 | 业务 ID |
| id | string | 是 | 主键 ID |
| start | int | 是 | 记录开始位置 |
| limit | int | 是 | 每页限制条数,最大 200 |

### 请求参数示例

```json
{
    "bk_app_code": "esb_test",
    "bk_app_secret": "xxx",
    "bk_token": "xxx",
    "bk_supplier_account": "123456789",
    "bk_biz_id": 1,
    "id": "xxx",
    "start": 0,
    "limit": 10
}
```

### 返回结果示例

```json
{
    "result": true,
    "code": 0,
    "message": "",
    "data": {
        "count": 1,
        "info": [
            {
                "biz": {
                    "bk_biz_id": 1,
                    "bk_biz_name": "test",
                    "bk_biz_maintainer": "admin",
                    "bk_biz_productor": "admin"
                },
                "host": {
                    "bk_host_id": 1,
                    "bk_host_name": "nginx-1",
                    "bk_host_innerip": "10.0.0.1",
                    "bk_cloud_id": 0
                },
                "module": {
                    "bk_module_name": "module-test"
                },
                "set": {
                    "bk_set_name": "set-test"
                }
            }
        ]
    }
}
```

### 返回结果参数说明

| 字段 | 类型 | 描述 |
|-----------|-----------|-----------|
| result | bool | 请求成功与否，true:请求成功，false:请求失败 |
| code | string | 组件返回错误编码，0  表示 success，>0 表示失败错误 |
| message | string | 请求失败返回的错误消息 |
| data | object | 请求返回的数据 |

#### data

| 字段 | 类型 | 描述 |
|-----------|-----------|-----------|
| count | int | 记录条数 |
| info | array | 主机实际数据 |

#### data.info

| 字段 | 类型 | 描述 |
|-----------|-----------|-----------|
| biz | dict | 主机所属的业务信息 |
| set | dict | 主机所属的集群信息 |
| module | dict | 主机所属的模块信息 |
| host | dict | 主机自身属性 |
