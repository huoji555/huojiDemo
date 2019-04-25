###### 1.人生第一个存储过程
```
CREATE DEFINER = `root`@`localhost` PROCEDURE `NewProc`(INOUT `left1` varchar(20),INOUT `right1` varchar(20),INOUT `feed1` varchar(20))
BEGIN
	DECLARE leftlen,rightlen,feedlen INT;
	SET leftlen = len(leftl);
	SET rightlen = len(rightl);
	SET feedlen = len(feedl);
	
	IF not EXISTS (select autocode from autocode where autocode like CONCAT(left1,'%') and autocode like CONCAT('%',right1)) THEN
		insert into autocode (autocode) values ( CONCAT(left1,feed1,right1));
		select CONCAT(left1,feed1,right1) as autocode;
  ELSE 
		insert into autocode 
		select CONCAT(left1,max(substring(autocode,leftlen+1,feedlen))+1,right1) from autocode where autocode like CONCAT(left1,'%') and autocode like CONCAT('%',right1);
		delete from autocode where autocode like CONCAT(left1,'%') and autocode like CONCAT('%',right1)
		and autocode not in (select max(autocode) from autocode where autocode like CONCAT(left1,'%') and autocode like CONCAT('%',right1));
		select max(autocode)  as autocode  from  autocode where autocode like CONCAT(left1,'%') and autocode like CONCAT('%',right1);
set feedlen = 2323;
	END IF;
   
END;
```
<br>

###### 2.存储过程中遇到的问题，记录一下

连接符CONCAT：很多内容是不允许`+`的，需要连接符

Mysql中的获取当前日期不能用`getDate()`,而应该选用`Now()`;

Mysql中测量两个日期之间的天数，需要用 `TIMESTAMPDIFF(MINUTE,Astartdate,now())` 这个函数

Mysql中给变量赋值时，不能像SqlServer中的`=`,而是应该选用`into`

Mysql中的`CONVERT`,`CAST`,可用`ROUND(X,Y)`代替

Mysql中的`return`,一般用`label:BEGIN`作为开头，`Leave label`作为返回语句

Mysql中转义存储过程和函数时，默认设置会报错，需要一句`et global log_bin_trust_function_creators=TRUE;`

Mysql中字符串计算长度时，用`Length()`,里边有别的字符时，可以用`CHAR_LENGTH()`,否则一个汉字是占3个字符长度，会造成误差
