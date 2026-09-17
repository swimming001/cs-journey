
3.  harness:外部测试，管理系统
    docker:环境容器，把程序装进稳定容器
    agent:做事情的主体


1. 数据--->OLTP(Mysql)-DI(data ingestion)->DL(data lake)-->ETL(extract,transform,load)-->DW(data warehouse)--OLAP-->BI(business intelligence)
    0. 数据
        (1)例子:CRM(customer relationship management)客户,HRMS(human resource management system)员工,ERP(enterprise resource planning)企业资源,IOT(internet of things)物联网
    1. OLTP(online transaction processing)
        注重ACID(atomicity,consistency,isolation,durability)
        (2)例子:淘宝购买业务，微信发信息
    2. OLAP(online analytical processing)
        (2)例子:年龄与购买力的关系
    3. DI:从数据库中获取数据
        (1)how:(1)batch:定时批处理
                    1. 例子:airflow
               (2)straming:数据产生立刻被处理=real-time processing
                    1. 例子：Kafka,flink,spark streaming
               (3)CDC(change data capture):只捕获数据库中发生变化的数据
                    1. 例子:debezium
    4. ELF：删选数据
    5. DL:数据获得的临时库
        (1)例子:Amazon s3
    5. DW：经过删选后的临时库=DSA(data staging area)
        (1)例子:CDW(cload data warehouse):snowflake,bigquery,redshift
    3. data integration:数据集成，数据怎么统一整合成一个外模式
   
