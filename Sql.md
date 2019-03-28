### 1.人生第一个存储过程
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
