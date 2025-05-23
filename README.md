# 简易网络key-value数据库
## 💻从源代码构建 How to build
### 如何运行？   
• 克隆此仓库   
• 安装 eclipse 或 IntelliJ IDEA 2024.3.5   
• 通过上述软件打开源码文件夹   
• 先启动一个**Server**服务端，再启动**Client**客户端（可多开）。      
## 具体功能：   
首先，你可以使用 ```set [名字] [内容] ``` 来设置一个包含内容的词，然后可以使用 ```get [名字]``` 来获取该词的内容。   
如果你觉得该词没有用了，可以使用 ```del [名字]``` 来删除这个量。   

同时，该程序还实现了哈希类型的设置键值对方式（即一个名字中可以包含多个键值对）：   
```hset [名字] [键名] [值]``` 为在 **[名字]** 中设置 **[键名]** 的内容为 **[值]**。   
```hget [名字] [键名]``` 为获取 **[名字]** 中 **[键名]** 的内容。   
```hdel [名字] [键名]``` 为删除 **[名字]** 中的 **[键名]** 。   
```hdel [名字]``` 为完全删除 **[名字]** 中的所有值。
***
当然，这些数据都可以长久保存下来（同一台电脑），所以你可以查找上一次保存的值。
***
其次，该程序实现了双向链表的基本功能：    
你可以通过 ```lpush [名字] [内容]``` 来将 **[内容]** 储存在 **[名字]** 这个链表中的第一个位置，如果没有创建过该链表，程序将会自动生成一个以 **[名字]** 为名字的链表。   
那既然叫双向链表，当然可以在最后一个位置存放数据啦~使用 ```rpush [名字] [内容]``` 就可以将 [内容] 储存在 [名字] 链表的最后一个位置。   
如果要查看某个链表的某些位置的数据，使用 ```range [名字] [从哪开始] [到哪结束]``` 即可   
例如：```range score 0 1``` 为查看score链表中第一位到第二位的数据内容。   
如果要查看某个链表的大小（即包含多少数据），通过 ```len [名字]``` 就可以获取该链表所保存的数据个数。   
有保存，那肯定要有删除功能， ```lpop [名字]``` 和 ```rpop [名字]``` 分别指删除链表第一位和最后一位的数据。   
如果要删除整个链表则使用 ```ldel [名字]``` 即可。   
***
还有一些其他指令~   
输入 ```help``` 可以查看所有可以使用的指令。   
输入 ```help [指令名称]``` 可以单独查看该指令。   
```ping``` 心跳指令，会响应**PONG**   
***
为了方便修改端口号，该程序将端口号单独放在 *Port.properties* 文件中，因此可以直接修改 *Port.properties* 中port变量的值以达到修改端口号的目的。   
每次运行程序时程序都会记录连接程序的ip地址并保存在 Log文件夹 的 *data.log* 文件中，而且，一旦程序出现意外的报错时不会直接退出而是输出报错类型同时保存在 *data.log* 文件里。
