# Apache-logs-move-AWS-s3-Bucket
#!/bin/bash
log_file_ext=$1
DATE=`date +%Y-%m-%d`
DATE1=`date +%Y-%m-%dT%HZ`
cd /usr/local/apache2/logs && tar -cvzf /temp/log_apache$DATE1.tar.gz *.$log_file_ext
s3cmd put /temp/log_apache$DATE1.tar.gz s3://magicsw-apache-prodlogs/vpc-magicsw-apache-appserver1/$DATE/ >> /temp/s3copystus.log 2>&1
rm -rf /temp/log_apache$DATE1.tar.gz

