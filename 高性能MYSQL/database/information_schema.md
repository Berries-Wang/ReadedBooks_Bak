## information_schema 用于存储数据库元数据(关于数据的数据)，例如数据库名、表名、列的数据类型、访问权限等。

### CHARACTER_SETS                        
### COLLATIONS                            
### COLLATION_CHARACTER_SET_APPLICABILITY 
### COLUMNS 
|--------------------------|---------------------|------|-----|---------|-------+
| Field                    | Type                | Null | Key | Default | comment |
|--------------------------|---------------------|------|-----|---------|-------|
| TABLE_CATALOG            | varchar(512)        | NO   |     |         | 包含该列的表所属的目录的名称。该值始终为def。|
| TABLE_SCHEMA             | varchar(64)         | NO   |     |         |包含字段所在数据库的名称      |
| TABLE_NAME               | varchar(64)         | NO   |     |         |包含字段所在表的名称       |
| COLUMN_NAME              | varchar(64)         | NO   |     |         |字段的名称       |
| ORDINAL_POSITION         | bigint(21) unsigned | NO   |     | 0       |表中字段的位置       |
| COLUMN_DEFAULT           | longtext            | YES  |     | NULL    |字段的默认值       |
| IS_NULLABLE              | varchar(3)          | NO   |     |         |字段可为空性       |
| DATA_TYPE                | varchar(64)         | NO   |     |         |字段数据类型       |
| CHARACTER_MAXIMUM_LENGTH | bigint(21) unsigned | YES  |     | NULL    |值包含类型名称以及可能的其他信息，例如精度或长度       |
| CHARACTER_OCTET_LENGTH   | bigint(21) unsigned | YES  |     | NULL    |对于字符串列，最大长度（以字符为单位）       |
| NUMERIC_PRECISION        | bigint(21) unsigned | YES  |     | NULL    |对于字符串列，最大长度（以字节为单位）       |
| NUMERIC_SCALE            | bigint(21) unsigned | YES  |     | NULL    |对于数字字段，数字精度|
| DATETIME_PRECISION       | bigint(21) unsigned | YES  |     | NULL    |对于时间字段，小数秒精度 |
| CHARACTER_SET_NAME       | varchar(32)         | YES  |     | NULL    |对于字符串字段，字符集名称|
| COLLATION_NAME           | varchar(32)         | YES  |     | NULL    |对于字符串字段，排序规则名称       |
| COLUMN_TYPE              | longtext            | NO   |     | NULL    |字段数据类型|
| COLUMN_KEY               | varchar(3)          | NO   |     |         |名称是否已建立索引|
| EXTRA                    | varchar(30)         | NO   |     |         |有关给定字段的任何其他可用信息|
| PRIVILEGES               | varchar(80)         | NO   |     |         |您对该字段的权限|
| COLUMN_COMMENT           | varchar(1024)       | NO   |     |         |字段定义中包含的任何注释|
| GENERATION_EXPRESSION    | longtext            | NO   |     | NULL    |对于生成的字段，显示用于计算列值的表达式|
|--------------------------|---------------------|------|-----|---------|-------|                       
### COLUMN_PRIVILEGES                     
### ENGINES                               
### EVENTS                                
### FILES                                 
### GLOBAL_STATUS                         
### GLOBAL_VARIABLES                      
### KEY_COLUMN_USAGE                      
### OPTIMIZER_TRACE                       
### PARAMETERS                            
### PARTITIONS                            
### PLUGINS                               
### PROCESSLIST                           
### PROFILING                             
### REFERENTIAL_CONSTRAINTS               
### ROUTINES                              
### SCHEMATA                              
### SCHEMA_PRIVILEGES                     
### SESSION_STATUS                        
### SESSION_VARIABLES                     
### STATISTICS                            
### TABLES                                
### TABLESPACES                           
### TABLE_CONSTRAINTS                     
### TABLE_PRIVILEGES                      
### TRIGGERS                              
### USER_PRIVILEGES                       
### VIEWS                                 
### INNODB_LOCKS                          
### INNODB_TRX                            
### INNODB_SYS_DATAFILES                  
### INNODB_FT_CONFIG                      
### INNODB_SYS_VIRTUAL                    
### INNODB_CMP                            
### INNODB_FT_BEING_DELETED               
### INNODB_CMP_RESET                      
### INNODB_CMP_PER_INDEX                  
### INNODB_CMPMEM_RESET                   
### INNODB_FT_DELETED                     
### INNODB_BUFFER_PAGE_LRU                
### INNODB_LOCK_WAITS                     
### INNODB_TEMP_TABLE_INFO                
### INNODB_SYS_INDEXES                    
### INNODB_SYS_TABLES                     
### INNODB_SYS_FIELDS                     
### INNODB_CMP_PER_INDEX_RESET            
### INNODB_BUFFER_PAGE                    
### INNODB_FT_DEFAULT_STOPWORD            
### INNODB_FT_INDEX_TABLE                 
### INNODB_FT_INDEX_CACHE                 
### INNODB_SYS_TABLESPACES                
### INNODB_METRICS                        
### INNODB_SYS_FOREIGN_COLS               
### INNODB_CMPMEM                         
### INNODB_BUFFER_POOL_STATS              
### INNODB_SYS_COLUMNS                    
### INNODB_SYS_FOREIGN                    
### INNODB_SYS_TABLESTATS 