# 毒 app
https://m.poizon.com/ 


## 2019-9-8 更新

💫最近在学习签名加密算法之类的东西, 发现这里的加密具有明显的 md5 特征, 因此尝试了一下直接用 md5 进行加密, 发现是正确的..... 代码如下 👇

```python 

si = get_sign_string({"recommendId": "73", "lastId": ""})
# sign = func(si)
import hashlib
m = hashlib.md5()
m.update(si.encode("utf8"))
sign = m.hexdigest()
print(sign)
res = requests.get(url.format(sign))
print(res.text)

```

毒 app sign 签名 js 解密的 python 复写版本

复写的原因:
    使用 js 执行速度较慢, 依赖 node 环境; 因此对于简单的加密可以尝试复写
    也可以加深对 js 加密及一些函数的理解

注意点: 
    js 的位左移 << 与 python 中的不一样
    这个是 python 的问题, 因为大多数编程语言执行结果与 js 都是一致的
    
    参考: https://blog.csdn.net/pzqingchong/article/details/77991187

解决上述问题:

    方式一是使用 shell 脚本执行位移, 发现返回结果是无符号的.....而且其它的执行结果貌似与 python 是一致的(失败)

    方式二是使用 execjs 编译一个 js 函数, 直接执行(使用)

    其它方式比如调用 node\ 调用其它语言等等都是可以的
    

