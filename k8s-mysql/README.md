# 部署mysql master-slave

# 创建命名空间
    kubectl create namespace mysql-space
    
 # mysql master slave服务
    kubectl create -f  mysql-master-rc.yaml
     kubectl create -f  mysql-master-svc.yaml
     kubectl create -f  mysql-slave-rc.yaml
     kubectl create -f  mysql-slave-svc.yaml
     
# 验证服务是否正常
     kubectl get pod -n mysql-space
     
# 进入master给slave库授权
     kubectl exec -n mysql-space mysql-master-rc-2ssgh -- mysql -uroot -pmysql123
     
     mysql> GRANT REPLICATION SLAVE ON *.* to 'repl'@'%' IDENTIFIED  by 'repl123';
     
     mysql>  show master status;
     +------------------+----------+--------------+------------------+-------------------+
     | File             | Position | Binlog_Do_DB | Binlog_Ignore_DB | Executed_Gtid_Set |
     +------------------+----------+--------------+------------------+-------------------+
     | mysql-bin.000003 |     1032 |              | mysql            |                   |
     +------------------+----------+--------------+------------------+-------------------+
  
 # slave库启动同步功能   
     [root@master k8s]# kubectl exec -ti -n mysql-space mysql-slave-rc-lhg47 -- mysql -u root -pmysql123
     
     mysql> change master to master_host='mysql-master-svc.mysql-space',master_user='repl',master_password='repl123',master_log_file='mysql-bin.000003',master_log_pos=1032 ;
     mysql>  start slave;
     

     # 查看状态是否正常，如果没有错误信息，那就ok
     mysql> show slave status \G;    