# 把img镜像挂载到文件系统
 
   把img镜像挂载到文件系统

## 使用fdisk查看分区信息
  
  `fdisk xxxx.img`
  p 打印分区信息,记住分区起始扇区
  
  或
  `fdisk -lu xxx.img`
  可直接打印分区信息
 
## mount分区
    
	`mount -o loop,offset=xxxx xxxx.img      /mnt/ `
	
	offset等于分区起始扇区x扇区大小
	(这里特别注意loop,offset  之间有逗号且不能有空格) 