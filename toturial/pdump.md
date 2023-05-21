# pdump 简介
`pdump` 是一个可以导入导出角色数据的GM命令，需要3级GM权限。

该命令可以把一个角色的数据导出，再根据这个角色导出的数据，创建出新的角色，创建新角色是没有数量限制的。
也就是说，导出的角色数据成了一个角色模板，可以根据这个模板无限制的创建新角色。

# 常见使用场景
1. 可以用别人分享出来的模板，来快速的创建大量复杂的账号出来，这对于我们使用机器人来说，是非常有用的。
2. 用于排查线上问题，比如某个角色的数据出现了BUG，我们可以导出这个角色的数据，再创建一个新角色，来复现BUG。
3. GM可以给玩家进行数据迁移，比如A玩家把他号里的一个角色卖给了B玩家，那么GM可以把这个角色的数据导出，再导入到B玩家的账号里（再把A账号里的角色删除）。

# 使用方法

## 导出角色数据
```
pdump write <文件名> <角色名或GUID>
```
* 文件名：任意，可以有后缀，也可以无后缀，填什么名字，导出来的文件就是什么名字，不会额外添加后缀。
* 角色名或GUID：二选一，角色名就是角色的名字，GUID是角色的唯一ID，可以在游戏里用 `.guid` 命令查看。

导出后的数据会在服务器程序的根目录，也就是 exe 所在目录。

示例：
假如我们要导出的角色名是 `苗人凤`，导出到文件 `苗人凤.txt`，那么命令是：
```
pdump write 苗人凤.txt 苗人凤
```

## 导入角色数据
```
pdump load <文件名> <账号> [新角色名] [新GUID]
```
* 账号：就是登陆游戏时用的账号。
* 其他参数：同上，不再解释。

中括号里的参数是可选的：
* 如果不填新角色名，创建出的新角色是和原来的一样的，第一次登陆时会提示改名。
* 如果不填新GUID，系统会自动生成一个新的GUID。（建议永远让系统生成，自己填需要确保数据库里没有重复的GUID）

示例：
假如我们要导入的账号是 `test`，导入的文件是 `苗人凤.txt`，那么命令是：
```
pdump load 苗人凤.txt test
```

> 注：以上命令都不需要是要导出的角色或账号，完全可以用一个第3方的GM账号来导入导出某个角色和账号的数据。