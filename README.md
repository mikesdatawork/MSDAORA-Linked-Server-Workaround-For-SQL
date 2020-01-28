![MIKES DATA WORK GIT REPO](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_01.png "Mikes Data Work")        

# MSDAORA Linked Server Workaround For SQL
**Post Date: October 10, 2007**        



## Contents    
- [About Process](##About-Process)  
- [SQL Logic](#SQL-Logic)  
- [Build Info](#Build-Info)  
- [Author](#Author)  
- [License](#License)       

## About-Process

<p>I ended up installing the 32bit Oracle Client to get the Provider: OraOLEDB.Oracle
my link between 64bit SQL Server to a 32bit Oracle server works great.
here's my full link scripted out.
hope it's useful</p>      


## SQL-Logic
```SQL

EXEC master.dbo.sp_addlinkedserver @server = N'OraLinkServer', @srvproduct=N'Oracle', @provider=N'OraOLEDB.Oracle', @datasrc=N'MyServer.MyDomain.COM'
EXEC master.dbo.sp_addlinkedsrvlogin @rmtsrvname=N'OraLinkServer',@useself=N'False',@locallogin=NULL,@rmtuser=N'MyUser',@rmtpassword='MyPassword'
GO
EXEC master.dbo.sp_serveroption @server=N'OraLinkServer', @optname=N'collation compatible', @optvalue=N'true'
GO
EXEC master.dbo.sp_serveroption @server=N'OraLinkServer', @optname=N'data access', @optvalue=N'true'
GO
EXEC master.dbo.sp_serveroption @server=N'OraLinkServer', @optname=N'dist', @optvalue=N'false'
GO
EXEC master.dbo.sp_serveroption @server=N'OraLinkServer', @optname=N'pub', @optvalue=N'false'
GO
EXEC master.dbo.sp_serveroption @server=N'OraLinkServer', @optname=N'rpc', @optvalue=N'false'
GO
EXEC master.dbo.sp_serveroption @server=N'OraLinkServer', @optname=N'rpc out', @optvalue=N'false'
GO
EXEC master.dbo.sp_serveroption @server=N'OraLinkServer', @optname=N'sub', @optvalue=N'false'
GO
EXEC master.dbo.sp_serveroption @server=N'OraLinkServer', @optname=N'connect timeout', @optvalue=N'0′
GO
EXEC master.dbo.sp_serveroption @server=N'OraLinkServer', @optname=N'collation name', @optvalue=null
GO
EXEC master.dbo.sp_serveroption @server=N'OraLinkServer', @optname=N'lazy schema validation', @optvalue=N'false'
GO
EXEC master.dbo.sp_serveroption @server=N'OraLinkServer', @optname=N'query timeout', @optvalue=N'0′
GO
EXEC master.dbo.sp_serveroption @server=N'OraLinkServer', @optname=N'use remote collation', @optvalue=N'true'
```

[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

[![Gist](https://img.shields.io/badge/Gist-MikesDataWork-<COLOR>.svg)](https://gist.github.com/mikesdatawork)
[![Twitter](https://img.shields.io/badge/Twitter-MikesDataWork-<COLOR>.svg)](https://twitter.com/mikesdatawork)
[![Wordpress](https://img.shields.io/badge/Wordpress-MikesDataWork-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

   
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Mikes Data Work](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_02.png "Mikes Data Work")

