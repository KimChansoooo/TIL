# Fuction That Returns The Day Of Week
> 요일을 리턴하는 함수

**WEEKDAY(date)**

date의 weekday를 반환 (`0` = Monday, `1` = Tuesday, … `6` = Sunday)
</br> * date가 null인 경우 null을 반환

[//]: # (Returns the weekday index for ***`date`*** &#40;`0`= Monday,`1` = Tuesday, …`6`= Sunday&#41;. Returns `NULL` if ***`date`*** is `NULL`.)

```mysql
mysql> SELECT WEEKDAY('2008-02-03 22:23:00'); -- 6(일)
mysql> SELECT WEEKDAY('2007-11-06');          -- 1(화)
```


**DAYOFWEEK(date)**

date의 weekday를 반환 (`1` = Sunday, `2` = Monday, …, `7` = Saturday)
</br> * date가 null인 경우 null을 반환

[//]: # (Returns the weekday index for ***`date`*** &#40;`1` = Sunday, `2` = Monday, …, `7` = Saturday&#41;. These index values correspond to the ODBC standard. Returns `NULL` if ***`date`*** is `NULL`.)

```mysql
mysql> SELECT DAYOFWEEK('2024-04-15');          -- 2(월)
```

<br/></br>
</br> [try] [W3School](https://www.w3schools.com/mysql/trymysql.asp?filename=trysql_func_mysql_dayofweek "Try Function")
</br> [ref.] https://dev.mysql.com/doc/refman/8.3/en/date-and-time-functions.html#function_dayofweek
