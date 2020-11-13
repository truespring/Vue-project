# Vue-project

## Vue로 만드는 todo-app

### 테이블 쿼리문

``` bash
CREATE TABLE t_todo(
	i_todo INT UNSIGNED PRIMARY KEY AUTO_INCREMENT,
	todo VARCHAR(255) NOT NULL,
	r_dt DATETIME DEFAULT NOW()
);
```