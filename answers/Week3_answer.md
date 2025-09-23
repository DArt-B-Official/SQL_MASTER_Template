~~~sql
SELECT member_id, name,
       (CASE
           WHEN join_date IS NULL THEN '미가입'
           WHEN join_date IS NOT NULL THEN '가입완료'
        END) AS join_status
FROM Member
ORDER BY name;
~~~

	•	CASE ~ WHEN ~ THEN ~ ELSE ~ END 구문은 조건 분기를 위해 사용합니다.
	•	여기서는 join_date 값이 비어 있으면 "미가입", 값이 있으면 "가입완료"로 표시합니다.
	•	마지막 ORDER BY name;은 회원 이름 기준으로 정렬하는 부분입니다.
