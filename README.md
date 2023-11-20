最近发现我连lab很卡，用的广电宽带，后来发现联通手机网ping lab延迟不到250ms，而且还很稳定。而广电宽带经常卡死，ssh连其他海外云服务器也有这个问题，ssh连接不稳定容易被服务器拒接连接，很是头疼，修改配置文件的机会都没有。

具体来说想要优化考试或者lab的稳定度（延迟应该是优化不了的了）有两种方式：

1 可以在考试的时候先连上云服务器的服务将本地的流量全部转发到服务器上面再连上考试提供的连接包就可以了，很稳定。但是有一个最大的风险是可能服务器的IP突然被封了，这估计是和具体的云服务器提供商和使用方法相关的。

2 直接用云服务器作为考试连接lab的主机，在里面操作考试，笔记和OSED的逆向什么的可以在本地操作，监考连接肯定是要在本地机器上运行了。

课程lab远程ip是欧洲的机房，考试用的机房不知道，和lab相同的可能性很大，所以尽量还是选择香港节点或者新加坡节点吧（这样用云服务器作为主机的方式延迟就低不少了），不然就洛杉矶（可能优化比较好），或者直接买在lab同一个服务商。如图，lab的机房是OVH提供的，具体的线路没有测试，推荐自行测试一遍（下载好课程的连接包后会显示远程ip）。

![图片](https://github.com/tuxsec/-blog/assets/26221848/d4d7f005-7019-4312-8fec-b41552241f07)


期间试了gigsgigs，cloudcone，阿里云，oracle，AWS。

gigs，试了洛杉矶节点，还是很卡（宽带的锅），群里别人就很流畅还很快，当时没发现我的宽带有问题所以立马退款了，流量使用量低于1%，七天之内就能退。

cloudcone和gigs差不多，也是洛杉矶节点，优点是非常便宜，延迟比gigs高一点，直接用它的远程桌面做考试用的客户端延迟也比较高，耐心好的应该能接受，这种方式推荐使用香港的节点，cloudcone只有洛杉矶的节点。也是申请退款了；

阿里云香港的节点，很稳定，延迟也和裸连lab差不多，推荐流量计费模式，每小时扣一次费用+流量费1元1G，可以考试的时候再开，推荐配置好之后存到快照里面（一个月1元的快照费用，快照单价0.136/G/月，5g以下免费，ubuntu的图形版+加配置好8g左右，如果精简一下应该是可以5g以下的，如果没有图形界面就不能用第二种方式考试了，OSED需要全程远程桌面用windbg调试），考试的时候重新开一个机子把快照导入就行了，据说OSCP考一天试需要30块的流量费，但是新用户可以免费试用，非常推荐新用户用。

oracle 韩国节点，连上lab延迟400ms，非常稳定地400ms，非常不适合没有耐心的人用。优点：免费。

![图片](https://github.com/tuxsec/-blog/assets/26221848/f946069e-d6fa-4540-8baa-f5695307b1d5)


AWS没有香港节点，新用户可以试用三个月（还是一年？）最好有一张visa或者万事达的信用卡方便注册，中信的借记卡注册不了（考试付费的时候它也用不了，我办了一张万事达的一张visa的）据说中国银行的visa借记卡可以注册（没办到，上海或者周边的同学可以直接在上海中行的公众号里面办，只能邮寄到上海范围内）有visa信用卡的同学就不用担心了。

AWS选的是新加坡节点，裸ping 100ms多延迟（图一），相比阿里云的香港节点（80多ms）还是高了一点，刚开始也是80多，截图的时候变成130多了（奇怪）。

图一：裸ping，有一些丢包。

![图片](https://github.com/tuxsec/-blog/assets/26221848/831c495c-882e-4308-a800-9421b654bac9)


图二：连上lab环境后，延迟很低。
![图片](https://github.com/tuxsec/-blog/assets/26221848/6e83ffb1-0432-4e67-929a-dbe0699a4d83)


最终还是AWS完胜，这个延迟和联通4g差不多，够流畅考试了。

最后推荐阿里云的和AWS的。
省略了很多配置的过程。本来是想在b站和简书上面发的，都被锁定了。

具体的服务器相关配置可以来群里交流，不是我建的群，好多blog的作者都在里面，氛围还不错，课程提问也可以来。

https://discord.com/invite/BjBWym2TMc
