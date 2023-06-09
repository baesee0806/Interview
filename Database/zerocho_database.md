# SQL

---

표준 언어는 ANCI SQL이다.

database cheatSheet를 참고 하는게 좋다.

MySQL 설치

```tsx
터미널 실행후
**brew install mysql**
```

- MySQL을 시작합니다.

```tsx
mysql.server start
```

- MySQL을 시작 후 기본 설정을 시작합니다.

```tsx
mysql_secure_installation;
```

- 순서대로 아래 질문들이 나오면 y 또는 n을 입력하여 설정해 줍니다.
  - 비밀번호 복잡도 검사 과정 (n)
  - 비밀번호 입력 & 확인익명 사용자 삭제 (y)
  - 원격 접속 허용하지 않을 것인가? (y)
  - test DB 삭제 (n)
  - previlege 테이블을 다시 로드할 것인지 (y)
  - 설정을 마치면 All done! 메세지가 출력됩니다.

사용하기

- bash에 다음 명령어를 입력하면 MySQL을 사용할 수 있습니다.
  ```tsx
  mysql -u root -p
  ```

추가설정

- MySQL 서버가 재부팅 상관없이 켜져있게 합니다. (bash에 입력)
  ```tsx
  brew services start mysql
  ```

## 정규화

### Key

- PK(기본키, primary key) 고유의 값으로 row를 구분해주는 키
- FK(외래키, foreign key) 다른테이블의 키를 사용하는것
- 복합키(Composite Key, 두 개 이상의 키가 기본키가 되는 것)

1정규화

1. 각항에 쪼갤수 없는 데이터가 들어가야 한다
2. id 값이 필요한 이유는 각 row의 값을 가져올때 고유의 값이 필요하기 떄문
3. uuid 사용하는 이유 겹칠일이 로또맞을 확률이기 떄문

### 1NF

한 컬럼에 값이 두 개...? → [X]

| 이름   | 전화번호                   |
| ------ | -------------------------- |
| 제로초 | 010-1234-5678010-2345-6789 |

---

가로로 배치..? → [X]

| 이름   | 전화번호1     | 전화번호2     |
| ------ | ------------- | ------------- |
| 제로초 | 010-1234-5678 | 010-2345-6789 |

---

[O]

| 이름   | 전화번호      |
| ------ | ------------- |
| 제로초 | 010-1234-5678 |
| 제로초 | 010-2345-6789 |

- 나중에 JOIN으로 합침

### ERD : 데이터 시각화 할때 좋다

관계 생각하기

1:1 일대일

1:N 일대다

사원:전화번호

M:N 다대다

사원 프로젝트

2정규화

- 복합키 모두에 종속되는지 체크

| 이름   | 언어 | 전화번호      |
| ------ | ---- | ------------- |
| 제로초 | JS   | 010-1234-5678 |
| 제로초 | TS   | 010-1234-5678 |
| 제로초 | JAVA | 010-1234-5678 |

3정규화

- Key가 아닌 컬럼들의 종속관계(A -> B, B -> C이고 A -> C인 관계가 있다면 A -> B, B -> C 두 개로 분리) 3단 논법으로 생각하자

| 아이디 | 이름   | 소속 | 서비스     |
| ------ | ------ | ---- | ---------- |
| 1      | 제로초 | 네   | 네이버웹툰 |
| 2      | 원초   | 카   | 카카오톡   |
| 3      | 투초   | 배   | 배민1      |

- 왜 소속이 아니라 서비스가 키?

역정규화

서비스에 따라서 정규형 위반이지만 편의성을 위해 허용

- JOIN, JOIN, JOIN
- 삽입, 수정, 삭제가 일어나지 않는 경우
- 서비스 따라 판단

### CREATE TABLE

DDL(Definition), DQL(Query), DML(Manipulation), DCL(Control), TCL(Transaction)

fk 없는 거 먼저 만들기

```
CREATE TABLE `zerocho`.`role` (
  `id` INT(11) UNSIGNED NOT NULL AUTO_INCREMENT,
  `name` VARCHAR(10) NOT NULL,
  `min_salary` INT UNSIGNED NOT NULL DEFAULT 2500,
  PRIMARY KEY (`id`),
  UNIQUE INDEX `name_UNIQUE` (`name` ASC) VISIBLE,
  UNIQUE INDEX `id_UNIQUE` (`id` ASC) VISIBLE)
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4;
```

ON UPDATE, ON DELETE 옵션들 기억하기

```
CREATE TABLE `employee` (
  `id` int unsigned NOT NULL AUTO_INCREMENT,
  `name` varchar(45) NOT NULL,
  `email` varchar(100) NOT NULL,
  `salary` int unsigned NOT NULL,
  `team` varchar(20) NOT NULL,
  `quit_date` date DEFAULT NULL,
  `created_at` datetime DEFAULT CURRENT_TIMESTAMP,
  `role_id` int unsigned DEFAULT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `email_UNIQUE` (`email`),
  KEY `employee_role_fk_idx` (`role_id`),
  CONSTRAINT `employee_role_fk` FOREIGN KEY (`role_id`) REFERENCES `role` (`id`) ON DELETE SET NULL ON UPDATE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci COMMENT='사원테이블'
```
