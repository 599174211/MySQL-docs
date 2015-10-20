Statement
=========
ִ��SQL������
##ͷ�ļ�
```cpp
#include <cppconn/statement.h>
```
##��
��һ���ӿ��ࡣֻ�������麯����
```cpp
sql::Statement *stmt;
// ��������
stmt = con->createStatement();
```
###��Ա����
```cpp
	virtual bool excute(const sql::SQLString& sql) = 0;
```
##Demo
```cpp
#include <iostream>

#include <mysql_driver.h>
#include <mysql_connection.h>
#include <cppconn/statement.h>
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

    Statement *stmt;
    stmt = con->createStatement();
    if (!stmt)
    {
        cout<<"stmt error"<<endl;
        return -1;
    }
	// ִ�и���SQL���
    stmt->execute("USE test");                                   // ѡ�����ݿ�
    stmt->execute("DROP TABLE IF EXISTS test");                  // ������Ѵ��ڣ���ɾ��
    stmt->execute("CREATE TABLE test(id INT, label CHAR(1))");   // ������
    stmt->execute("INSERT INTO test(id, label) VALUES(1, 'a')"); //��������

    delete stmt;
    delete con;
}
```
