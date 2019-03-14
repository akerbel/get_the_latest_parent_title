# get_the_latest_parent_title
MySQL stored procedure. Finds the highest parent in the category/menu tree.


DROP PROCEDURE IF EXISTS get_the_latest_parent_title;
DELIMITER %%
CREATE PROCEDURE get_the_latest_parent_title(IN id INT, OUT result VARCHAR(64))
	   BEGIN
       	 REPEAT
         	SELECT plid, link_title INTO id, result FROM menu_links WHERE mlid = id LIMIT 1;
         UNTIL id = 0 END REPEAT;
       END;
       %%
DELIMITER ;
CALL get_the_latest_parent_title(1216, @result);
SELECT @result;
