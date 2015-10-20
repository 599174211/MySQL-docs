PreparedStatement
=================
��һ������ġ���䡱�ࡣ
- Statement��ִ�е����ֻ���Ǿ�̬���ַ��� 
- PreparedStatement��ִ�е������Ժ��б���������ռλ��˼��ʵ�֣�

##ͷ�ļ�
```cpp
#include <cppconn/prepared_statement.h>
```
##��
```cpp
PreparedStatement *pstmt;
// ��������
pstmt = con->prepareStatement("INSERT INTO test(id, label) VALUES(?, ?)");
```
ͨ��Connector�����prepareStatement������������������������һ������ռλ����**?**����SQL��䡣
###���ռλ��
```cpp
pstmt->setInt(1, 2);       // ����һ��ռλ���������2
pstmt->setString(2, "b");  // ���ڶ���ռλ������ַ���"b"
```
###ִ��SQL
```cpp
pstmt->execute();
```

##Demo
```cpp
#include <iostream>

#include <mysql_driver.h>
#include <mysql_connection.h>
#include <cppconn/prepared_statement.h>
using namespace std;
using namespace sql;
int main()
{
    mysql::MySQL_Driver *driver;
    Connection *con;

    driver = mysql::get_mysql_driver_instance();
    if (!driver)
    {
        cout<<"dirver error"<<endl;
        return -1;
    }

    con = driver->connect("tcp://127.0.0.1:3306", "root", "123456");
    if (!con)
    {
        cout<<"conn error"<<endl;
        return -1;
    }

    con->setSchema("test");
    PreparedStatement *pstmt;
    pstmt = con->prepareStatement("INSERT INTO test(id, label) VALUES(?, ?)");
    if (!pstmt)
    {
        cout<<"prepared stmt error"<<endl;
        return -1;
    }
    pstmt->setInt(1, 2);
    pstmt->setString(2, "b");
    pstmt->execute();


    delete pstmt;
    delete con;
}
```
