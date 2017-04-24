## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/xushjie1987/xushjie1987.github.io/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/xushjie1987/xushjie1987.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.


`SDK最初的token报文内容：`
```
appKey填写真实的字符串appKey，SDK不需要考虑后续更新这个字段；
userId初始固定传数字0，SDK不需要考虑后续更新这个字段；
state初始固定字符串NEW，如果是DEBUG模式，则为DEBUG，SDK后续只有在DEBUG场景下会主动设置这个字段值为DEBUG；
threshold初始固定传数字100，SDK不需要考虑后续更新这个字段；
hashCode按照实际情况，填写SDK计算得到的hash码，数值类型，SDK不需要考虑后续更新这个字段；
isGray初始固定布尔类型false，SDK不需要考虑后续更新这个字段；
isOnce初始固定布尔类型false，SDK不需要考虑后续更新这个字段；
isDebug根据实际情况，如果是调试模式，那么布尔类型true，如果不是调试模式，那么布尔类型false，SDK需要根据是否调试模式而主动更新这个字段；
timeout和timestamp初始固定数值类型系统当前unix时间戳，两个值相等即可，注意，毫秒级别，不是秒级，SDK不需要考虑后续更新这个字段；
surviveAge初始默认值数字类型3即可，SDK不需要考虑后续更新这个字段；
minExpTime初始传一个空对象，但是不是null，即{}，SDK不需要考虑后续更新这个字段；
```
```json
    "token": {
        "appKey": "TESTIN_xxxxx",
        "userId": 0,
        "state": "NEW",
        "threshold": 100,
        "hashCode": 3,
        "timeout": 1491013806000,
        "isGray": false,
        "isOnce": false,
        "isDebug": false,
        "timestamp": 1491013806000,
        "surviveAge": 3,
        "minExpTime": {}
    }
```
`完整版的下拉配置报文结构：`
```json
{
    "appKey": "1d9cc6eb5-a728-4bad-b1a2-2ea2b39036d",
    "clientId": "3ea827d8e266fcfaf69b263aa3cab9f7",
    "appVersion": "1212121",
    "sdkVersion": "adfasfsdfewwerwe",
    "expVersionId": "0",
    "deviceinfo": {
        "osVersion": "7.0",
        "osVersionCode": "20",
        "platform": "iPhone OS",
        "packageName": "com.gome.com.cn",
        "language": "EN",
        "country": "EN",
        "deviceType": "iPhone",
        "deviceModel": "iPhone7",
        "displayWidth": "1242",
        "displayHeight": "2208",
        "mac": "F4:5C:89:89:EF:7B",
        "net": "wifi",
        "ip": "192.168.113.173",
        "referrer": "www.baidu.com",
        "url": "abtest.testin.cn",
        "browserName": "firefox",
        "browserVersion": "52"
    },
    "customerLabel": {
        "city": "Beijing",
        "gender": "male"
    },
    "token": {
        "appKey": "TESTIN_xxxxx",
        "userId": 0,
        "state": "NEW",
        "threshold": 100,
        "hashCode": 3,
        "timeout": 1491013806000,
        "isGray": false,
        "isOnce": false,
        "isDebug": false,
        "timestamp": 1491013806000,
        "surviveAge": 3,
        "minExpTime": {
        }
    }
}
```
`示例的响应报文结构：`
```json
{
    "errNo": 10001,
    "message": "未分配到可用的试验版本",
    "data": {
        "exps": [
            {
                "layerId": 111,
                "layerName": "默认层"
            },
            {
                "layerId": 112,
                "layerName": "层1"
            }
        ],
        "token": {
            "appKey": "TESTIN_xxxxx",
            "userId": 123456,
            "state": "RUNNING",
            "threshold": 20,
            "hashCode": 3,
            "timeout": 1491014806000,
            "isGray": false,
            "isOnce": false,
            "isDebug": false,
            "timestamp": 1491013806000,
            "surviveAge": 0,
            "minExpTime": {
                "11111": "2017-01",
                "22222": "2017-02",
                "33333": "2017-03"
            }
        }
    }
}
```
```
SDK需要处理的是：
读取响应报文中data字段中的token字段，然后解析state字段进行相应操作；
```






















