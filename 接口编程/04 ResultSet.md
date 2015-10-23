ResultSet
=========
SQL��䷵�صĽ����
##ͷ�ļ�
```cpp
#include <cppconn/resultset.h>
```
##��������
��`sql::Statement::executeQuery()`��`sql::PreparedStatement::executeQuery()`���ء�
���磺
```
sql::Connection *con;
sql::Statement *stmt;
sql::ResultSet *res;
// ...
con->setSchema("test");
// ...
stmt = con->createStatement();
res = stmt->executeQuery("SELECT id, label FROM test");
```
##��Ա����
###next
����bool���ͣ�����**����**�����������  

������ڲ���**�α�**������ŵ�ǰ�С��α���ʼλ��Ϊ��һ�У�ÿ��ִ����next�������α궼���ƶ�����һ�С�
##getXXX
|����|����ֵ|˵��
|-----|-----|-----
|getInt|int32_t|���ص�ǰ��ĳһ�е�ֵ��Ϊ����
|getString|SQLString|���ص�ǰ��ĳһ��ֵ��Ϊ�ַ���
|getUInt|uint32_t|......32λ�޷�������
|getInt64|int64_t|......64λ�з�������
|getUInt64|uint64_t|......64λ�޷�������
|getBoolean|bool|......bool����
|getBlob|std::istream|.......����������

**getXXX**��һϵ�к���������ȡ����ǰ��ĳһ��ֵ��**XXX**��ʾ�������͡�

��ϵ�ຯ�����������أ�
- ������������Ϊ��������ʾȡ�ڼ��е�ֵ��
- Ҳ����ʹ���ַ�����Ϊ������ȡ����Ӧ������ֵ��

����
```
while (res->next())
{
	cout << "id = "<<res->getInt(1)<<";label = "<<res->getString("label")<<endl;
}
```
