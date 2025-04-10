# LeetCode 规避限制，创建新进度方法

> 2025.02.17 测试有效



## 背景

众所周知，LeetCode 中进度是非常好用的一个功能。就我个人而言，每次求职准备阶段，都会开启一个新的进度，用于隔离之前的刷题记录。

![shot_3764](assets/image-20250410211919689.png)

然而却悲催地发现：


![shot_3765](assets/image-20250410212003713.png)

竟然暂时不支持创建新的进度了！据说是为了限制共享账号的情况，不过目前（2025.02.17）仍有绕过限制，创建进度的方法。



## 创建新进度方法

首先，获取 LeetCode 网站的 csrftoken。需要打开 Chrome 浏览器的 Inspect 面板，在 Application 下找到 Cookies，然后搜索 csrftoken，存下对应的 Value

![shot_3768](assets/image-20250410212600202.png)

然后切换到 Console Tab，输入下面的命令。注意将 csrftoken 替换为刚才复制的 value，以及修改你想要创建的进度的名字：

```
const options = {
    headers: {
        "content-type": "application/json",
        "x-csrftoken": "(PUT YOUR CSRF TOKEN HERE)",
        "x-requested-with": "XMLHttpRequest"
    },
    body: JSON.stringify({
        func: "create",
        name: "(PUT YOUR SESSION NAME HERE)"
    }),
    method: "PUT"
};
```

![shot_3771](assets/image-20250410212704609.png)

然后按回车执行。下一步再执行这行代码，就大功告成了！

```
fetch("https://leetcode.cn/session/", options)
```

![image-20250410212717403](assets/image-20250410212717403.png)

最终效果：（点击一下进度名字，即可切换当前的进度）

![shot_3773](assets/image-20250410212746782.png)

好用的话给个✨
