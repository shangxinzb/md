```bash
#!/bin/bash

base_dir=/home/backup
DATE=$(date +%Y%m%d)
time=$(date "+%Y-%m-%d_%H%M%S")
sql_file_name=koubei_$time.sql
echo $sql_file_name
compress_file_name=koubei_$time.tar.gz
echo $compress_file_name
cd $base_dir
mysqldump -ukoubei1 -pKoubei123!@ --databases koubei > $sql_file_name

tar -czvf $compress_file_name $sql_file_name
rm -f $sql_file_name

find ./ -type f -mtime +7 -exec rm -rf {} \;

scp $compress_file_name root@dev.sunchao.pro:/data/backup/$compress_file_name
scp $compress_file_name root@ceshi.1e2.cn:/mnt/resource/backup/$compress_file_name
```

