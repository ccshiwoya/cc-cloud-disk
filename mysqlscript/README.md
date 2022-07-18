
    	MySQL 数据库 和 相关表

===============

一、用户信息表（user_info）
------------
字段名		意义		类型

id		序号		bigint

user_name	用户名称		varchar(32)

nick_name	用户昵称		varchar(32)

phone		手机号码		varchar(16)

email		邮箱		      varchar(64)

password	密码		      varchar(32)

create_time	用户创建时间	  TIMESTAMP

二、文件信息表（file_info）
------------

字段名		意义		类型

id		序号		bigint

md5		文件md5		varchar(256)

file_id		文件id		varchar(256)

url		文件url		varchar(512)

size		文件大小		bigint

type		文件类型		varchar(32)

count		文件引用计数	int

三、用户文件列表（user_file_list）
------------

字段名		意义		类型

id		序号		int

user		文件所属用户	varchar(32)

md5		文件md5		varchar(256)

file_name		文件名字		varchar(128)

shared_status	共享状态		int

pv		文件下载量	int

create_time	文件创建时间	timestamp

四、用户文件数量表（user_file_count）
------------

字段名		意义		类型

id		序号		nt

user		文件所属用户	varchar(128)

count		拥有的文件数量	int

五、共享文件列表（share_file_list）
------------

字段名		意义		类型

id		序号		int

user		文件所属用户	varchar(32)

md5		文件md5		varchar(256)

pv		文件下载量	int

file_name		文件名字		varchar(128)

create_time	文件共享时间	timestamp
