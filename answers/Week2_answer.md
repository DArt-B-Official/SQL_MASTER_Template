## 문제 1

> **🧚다음 테이블을 생성하는 명령어를 실행했더니 오류가 발생했습니다. 오류의 원인이 되는 부분을 찾고, 그 이유를 설명하세요. 그리고 정상적으로 실행되기 위해 어디를 바꿔야 하는지 설명하세요.**

~~~sql
CREATE TABLE Member (
    member_id INT PRIMARY KEY,
    name VARCHAR(50),
    join_date NULL,
    email VARCHAR(100)
);
~~~



~~~
오류가 발생하는 부분 : 'join_date NULL'

이유 : 
데이터 타입이 지정되지 않았습니다. 
테이블을 생성할 때는 각 컬럼에 대한 자료형을 반드시 지정해야 합니다.
NULL은 'NULL 값을 허용한다'의 의미로 쓰일 뿐, 자료형이 아닙니다. 

정상 실행을 위해서 고치기 위해서는 
'join_date DATE NULL' 로 DATE 타입으로 지정해줘야 합니다. 
~~~



## 문제 2

> **🧚책에서는 `DELIMTER //` 를 사용했습니다. 만약 `DELIMITER &&` 또는 `DELIMITER !!`와 같이 다른 기호를 사용해도 실행이 될까요? 만약 된다면, 그 이유도 함께 설명해주세요.**

~~~sql
DELIMITER //
CREATE PROCEDURE testProc()
BEGIN
    SELECT 'Hello, MySQL!';
END //
DELIMITER ;
~~~



~~~
정답 : 실행된다. 
이유 :
'DELIMITER'는 MySQL 클라이언트가 명령어의 끝을 인식하는 구분자를 바꿀 때 사용하는 명령어이다.
원래 기본적으로는 세미콜론(;)을 사용하지만, 사용자가 원하는 아무 기호로도 바꿀 수 있다. 

중요한 것은 CREATE PROCEDURE 안의 세미콜론과 명령문의 종료를 구분하기 위해 다른 기호를 쓰는 것이다. 기호는 그냥 기호일뿐 중요하지 않다. 
~~~
