# esafenet-unlock 亿赛通在线离线解密
​
## 亿赛通在线全盘解密原理    
必要条件：加密文件可以在所在电脑正常打开，即在线状态。    
原理：亿赛通加密原理为劫持系统的读写，完成对指定后缀的透明加密和解密。    
核心思路：  
也就是说，亿赛通维护了可以正常读写指定后缀的程序进程清单，例如，winrar可以正常读取.rar文件，同时写入.rar文件，但是写入.rar时候是会被加密的，写入其他未知后缀则不会加密，所以可以使用winrar这样名称的程序去读取.rar文件，并写入为.rar.tmp,
这样.rar.tmp就是为未加密的文件。核心思路介绍到此。    
这样就产生了如下问题：    
1、文件被修改为.rar.tmp，如何改回来    
虽然可以手动改，但是过于麻烦，并且如果使用winrar直接修改名称，还是不行，会被加密，所以使用另一个程序负责将解密后的.rar.tmp还原为.rar，这样就完成了对rar的解密。    
2、文件后缀又不是全部都是rar    
大部分的文件后缀随机，例如a.doc，b.xls，所以为了让伪装的winrar能直接解密，可以将a.doc重命名为a.doc.rar，这样解密服务会认为是winrar在读取一个.rar的文件，提供解密。然后执行核心思路即可。    
3、文件很多，不是全部文件需要解密    
虽然我们可以完成上述两个程序的编写，但是如果文件个数过于庞大，例如几十万个文件，都执行一遍解密和重命名的工作，过于傻了，因此我们需要区分哪些是加密文件，哪些是非加密文件。  
使用工具hexed可以在线查看文件16进制，我们可以发现如果文件如果以 ??142365 开头，则可以认为文件被加密，直接执行解密工作就可以。  
如果说上面是理想状态的正常流程，那就存在另一种极端情况：加密文件离线，即无法在所在电脑打开，这时候我们需要进行离线解密。   
## 亿赛通离线部分解密
必要条件：需要准备一个未加密文件a.doc及对应解密文件，假如为a-jiemi.doc,同时准备好解密服务。   
原理：大佬通过算法直接算出加密密钥，然后用密钥解密全部文件。    

1、 a.doc和a-jiemi.doc要求
最好在1MB级别，不然计算密钥过程太长，或者数据太少都不太容易解出    
2、 解密服务在哪     
当然是站在大佬的肩膀上，调用解密方法就可以      
3、 有什么弊端   
不保证全部可以解密，测试过程中，发现存在无法解密的问题，可靠性在90%左右。    
同时幸运的话，可以直接通过加密文件恢复密钥，直接解密，相当于题解写在题面上。     

防止滥用，具体程序可以私聊qq 1191156989，付费付费

以上参考资料如下：   
https://www.cnblogs.com/MarsPanda/p/16404045.html     
https://m.yueqi168.com/weijiezhimi/146874.html    
https://github.com/UoUoio/YiSaiTong    
http://www.ramlife.org/2021/08/31/396.html     
​
