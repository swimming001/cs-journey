
4. 数学化:
    (1)关系模式 R(A1,A2,...,An)//R(U,D,DOM,F)
    (2)属性集合 U={A1,A2,...,An}
    (3)属性域 Di
    (4)元组 t={a1,a2,..,an}
    (5)关系 r(R)是子集D1* D2*...* Dn;


3. 关系数据语言(用于关系操作集合)：
    (1)关系代数:ISBL
    (2)关系演算 ：元组关系演算(ALPHA)/域关系演算(QBE)
    (3)结构化查询语言: SQL 具有关系代数和关系演算双重特点

2. 关系模型的三个组成部分:
    (1)Relational Data Structure        关系数据结构:relation，attribute，tuple
    (2)Relational Operations            关系操作集合：并，差，笛卡尔积，选择，投影
    (3)Relational Integrity Constraints 关系完整性约束：(entity integrity) 主键唯一，(referential integrity)外键引用有效，(user-defined integrity)用户定义完整

1. 数据库系统的三级模式？
    1. 内模式（Internal Schema）:how 存储数据在磁盘:b+ tree index;store page;
    2. 模式()：表，属性，键，约束，关系；数据库管理员设计的“整体逻辑视图”
    3. 外模式，不同权限n versus 用户view
    Q:为什么要设计三种模式呢？
        为了解耦；
        当用新的方法在磁盘存储数据时，其他模式不受影响；当新增表属性，外模式无影响
    A：实现数据独立性
        (1)物理数据独立性 Pysical Data Indenpence
        (2)逻辑数据独立性Logical Data Independence

0. 数据库:数据的集合
    由于不好管理，于是开发一个专门管理数据库的系统
    即用户-(SQL)->DBMS->DB->Drive
    1. DBMS 管理数据库的软件 e.MySQL,Oracle
        目的:增删改查，权限管理，备份恢复等
    2. Relational DB
        数据像表格，表通过关系连接
       NoSQL
        JSON{
            "name":"张三",
            "age":18,
            "hobby":["coding","music"]
            }

