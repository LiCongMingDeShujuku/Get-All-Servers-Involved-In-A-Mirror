![CLEVER DATA GIT REPO](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/0-clever-data-github.png "李聪明的数据库")

# 获取镜像中涉及的所有服务器
#### Get All Servers Involved In A Mirror
**发布-日期: 2015年10月13日 (评论)**

![#](images/##############?raw=true "#")

## Contents

- [中文](#中文)
- [English](#English)
- [SQL Logic](#Logic)
- [Build Info](#Build-Info)
- [Author](#Author)
- [License](#License) 


## 中文
这里有一些向你展示数据库镜像中涉及的服务器的快速sql逻辑。这不会显示哪个是Principal或Mirror，而只显示服务器名称。查询显示“Server1”和“Server2”加上“Witness”。它主要是为你提供服务器名称。


## English
Here’s some quick sql logic to show you the Servers involved in a database mirror. This does not show you which is Principal or Mirror, but only the server names. The query shows “Server1” and “Server2” plus the “Witness”, but that it. It’s meant to give you the Server names.

---
## Logic
```SQL
use master;
set nocount on
select
[Server1] = @@servername
,   [Server2] = replace(reverse(right(reverse(mirroring_partner_name), len(mirroring_partner_name) - charindex('.',reverse(mirroring_partner_name),10) + 0)), 'TCP://', '') ,   [Witness] = case
mirroring_witness_name
when '' then 'NOT CONFIGURED'
else replace(reverse(right(reverse(mirroring_witness_name), len(mirroring_witness_name) - charindex('.',reverse(mirroring_witness_name),10) + 0)), 'TCP://', '') end
from
master.sys.database_mirroring
where
mirroring_partner_name is not null


```



[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

- **李聪明的数据库 Lee's Clever Data**
- **Mike的数据库宝典 Mikes Database Collection**
- **李聪明的数据库** "Lee Songming"

[![Gist](https://img.shields.io/badge/Gist-李聪明的数据库-<COLOR>.svg)](https://gist.github.com/congmingshuju)
[![Twitter](https://img.shields.io/badge/Twitter-mike的数据库宝典-<COLOR>.svg)](https://twitter.com/mikesdatawork?lang=en)
[![Wordpress](https://img.shields.io/badge/Wordpress-mike的数据库宝典-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

---
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Lee Songming](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/1-clever-data-github.png "李聪明的数据库")

