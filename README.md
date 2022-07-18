# examiner

> 操作系统通知中心监控，可编写对应处理脚本

## 介绍

详细实现介绍见这篇推文：[不论微信钉钉还是什么软件，我写了个通用的消息监控处理机器人](https://mp.weixin.qq.com/s/-QDjgnKn_22DoeR2ti4iyA)

## 使用

```
1. clone 本仓库至本地
2. shell 终端执行命令查看电脑消息通知所在路径：cd `getconf DARWIN_USER_DIR`/com.apple.notificationcenter/db2
3. 修改 examiner/examiner/config/config.py DB_PATH 变量
```

接下来只需要在根目录构建自己的监控脚本就行，比如监控微信，建立文件命名为 `wechat_app.py`:

```python
from examiner import Examiner

app_names = ["Wechat"]
examiner_app = Examiner(app_names)
info_list = examiner_app.get_notifications()
for each in info_list:
    print(each)
```

输出：

```shell
{'title': 'test', 'subtitle': '', 'body': '测试消息监控', 'delivered_date': datetime.datetime(2022, 10, 20, 21, 40, 26, 428654), 'presented': 1, 'app_identifier': 'com.tencent.xinwechat', 'app_name': 'WeChat', 'md5': '75e24e2ccc502f01c101fcbd3637950b'}
```
