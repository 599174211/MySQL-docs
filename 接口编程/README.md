MySQL Connector/C++�ӿڱ��
============================
##ͷ�ļ�·��
```
include/
������ cppconn
��   ������ build_config.h
��   ������ config.h
��   ������ connection.h
��   ������ datatype.h
��   ������ driver.h
��   ������ exception.h
��   ������ metadata.h
��   ������ parameter_metadata.h
��   ������ prepared_statement.h
��   ������ resultset.h
��   ������ resultset_metadata.h
��   ������ sqlstring.h
��   ������ statement.h
��   ������ variant.h
��   ������ version_info.h
��   ������ warning.h
������ mysql_connection.h
������ mysql_driver.h
������ mysql_error.h
```
##���뻷��
��Ҫ����boost�⡣  
һ�ֿ���g++�ı���ѡ�
```makefile
CFLAGS  =  -I/usr/local/mysql/include \
           -I/usr/local/boost/include \
           -L/usr/local/boost/lib \
           -L/usr/local/mysql/lib \
           -Wl,-rpath=/usr/local/mysql/lib \
           -lmysqlcppconn \
```
���mysql�Ŀ�·��û�б��༭��**/etc/ld.so.conf.d/**Ŀ¼�У�Ҫ��rootȨ�ޣ�����ldconfig����ˢ�£��Ļ���  
����Ҫ��**-Wl,-rpath**ѡ��ָ����