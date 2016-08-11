+++
date = "2016-08-11T17:44:20+08:00"
description = ""
draft = false
tags = ["python","OptionParser"]
title = "python模块之OptionParser"
topics = []

+++

#### OptionParser

    !/usr/bin/env python
    coding=utf-8
    
    import sys
    import requests
    from optparse import OptionParser
    
    def parser():
    	parser=OptionParser()
    	parser.add_option("--dbs",action="store_true",dest="dbs",default=False,help="Fetch all the databases")
    	parser.add_option("--tables",action="store_true",dest="tables",default=False,help="Fetch all the tables")
    	parser.add_option("--columns",action="store_true",dest="columns",default=False,help="Fetch all the columns")
    	parser.add_option("--dump",action="store_true",dest="dump",default=False,help="Fetch all the dump")

    	parser.add_option("-D","--db_name",type="string",dest="db_name",help="Database name")
    	parser.add_option("-T","--table_name",type="string",dest="table_name",help="Table name")
    	parser.add_option("-C","--column_name",type="string",dest="column_name",help="Column name")
    	parser.add_option("--prefix",type="string",dest="column_name",help="Inject prefix")
    	parser.add_option("--suffix",type="string",dest="suffix",help="Sql Inject suffix")
    	parser.add_option("-u","--url",type="string",dest="url",help="url")

	    (options,args)=parser.parse_args(sys.argv)

	print options
	print options.dbs
	# print args
	
    def main(options):
	
    	if options.dbs:
    		print options
    	elif options.tables:
    		print options
    	elif options.columns:
    		pass
    	elif options.dump:
    		pass
    	else :
    		print "error"

	

    if __name__ == '__main__':
    	options=parser()
    	main(options)


###### add_option()参数说明：

- action：存储方式

- type：类型

- dest：存储的变量

- default：默认值

- help：帮助信息(默认有help参数)

###### parser.parse_args()函数：

1.默认参数是sys.argv[1:]

2.函数返回值是一个字典和一个列表

- options是一个字典，键值对

- args是一个列表





##### 类似sqlmap用法

sqlmap -u "url" --dbs

sqlmap -u "url" --tables -D "数据库名"

sqlmap -u "url" --columns -T "表名"  -D "数据库名"






