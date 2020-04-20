#### 函数的使用

```
查某一列数据的重复出现次数：=COUNTIF(B:B,B1)

判断值是否等于字符串：=IF(C2="Summer","VERÃO","INVERNO")

```

#### 生成SQL插入语句

```
=CONCATENATE("INSERT INTO tb_tm_hybird(ID, HYBIRD_NAME, HYBIRD_TYPE, LOAD_UNLOAD_LIMIT_TIME, SEASON, MOISTURE, P95, DATA_STATE, CRT_ID
, CRT_DATE ) VALUES(REPLACE ( UUID(), '-', '' ), '"&B3&"','"&H3&"','"&G3&"','"&I3&"','"&E3&"','"&D3&"', '10', '495452f729dc4486ae574b25db5a38f4', now());")
```

#### 生成SQL更新语句

```
=CONCATENATE("UPDATE TB_TM_HYBIRD H set MAIL_NAME = '"&D2&"', FEMAIL_NAME = '"&E2&"',LOAD_UNLOAD_LIMIT_TIME = '"&G2&"',MOISTURE = '"&I2&"',P95 = '"&H2&"' UPDATE_ID = '495452f729dc4486ae574b25db5a38f4', UPDATE_DATE = now() WHERE H.HYBIRD_NAME = '"&B2&"';")
```

