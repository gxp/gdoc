# cifs

smb

sudo mount -t cifs //nas-server/cifsShare /media/paul/cifsShare -o username=paulOnNAS,iocharset=utf8,file_mode=0777,dir_mode=0777,soft,user,noperm


# sync

rsync -ar
