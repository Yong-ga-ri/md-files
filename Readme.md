# DevGroup 객체에 대한 CRUD 정의 및 CRUD
- 작업 사항:
   - DevGroup 객체에 대한
       - create
       - FindOneByDevGroupCode
       - FindDevGroupList
       - Delete

## 테스트 방법
- `.source/application-mariadb`에서 데이터베이스를 `mvp_test`로 변경합니다.
- company 엔티티를 생성합니다 [[참고](https://gitlab.com/server.unirobotics/Gravity/-/merge_requests/387)]
- branch 엔티티를 생성합니다 [[참고](https://gitlab.com/server.unirobotics/Gravity/-/merge_requests/404)]
- DevGroup 엔티티를 생성합니다.
- [POST] `http://localhost:8080/api/dev-group/{branch_code}`으로 엔티티를 생성
    - example: `http://localhost:8080/api/group/1`
    - json Body
```bash
{
    "group_name": "group name"
}
```
- [GET] `http://localhost:8080/api/dev-group/{group_code}`로 생성된 엔티티를 조회합니다.
- [GET] `http://localhost:8080/api/role/`로 생성된 엔티티를 리스트를 조회합니다.
- [Delete] `http://localhost:8080/api/role/{role_code}`
    - [GET] `http://localhost:8080/api/role/`로 해당 엔티티가 삭제되었는지 확인합니다.

## 테스트 결과
- `http://localhost:8080/api/dev-group/{branch_code}` [POST]
```bash
{
    "code": 13,
    "branchLocation": {
        "code": 2,
        "company": {
            "auto_created_id": 1,
            "name": "sample",
            "created_on": "2022-05-03T14:38:19.256658",
            "updated_on": "2022-05-03T14:38:19.256676"
        },
        "branch_name": "branch field",
        "address": "address field",
        "created_on": "2022-05-03T14:38:44.692117",
        "updated_on": "2022-05-03T14:38:44.692132"
    },
    "group_name": "group name",
    "created_on": "2022-05-03T20:40:36.159099",
    "updated_on": "2022-05-03T20:40:36.159107"
}
```

- `http://localhost:8080/api/dev-group/{group_code}` [GET]
```bash
{
    "code": 13,
    "branchLocation": {
        "code": 2,
        "company": {
            "auto_created_id": 1,
            "name": "sample",
            "created_on": "2022-05-03T14:38:19.256658",
            "updated_on": "2022-05-03T14:38:19.256676"
        },
        "branch_name": "branch field",
        "address": "address field",
        "created_on": "2022-05-03T14:38:44.692117",
        "updated_on": "2022-05-03T14:38:44.692132"
    },
    "group_name": "group name2",
    "created_on": "2022-05-03T20:40:36.159099",
    "updated_on": "2022-05-03T20:40:36.159107"
}
```

- `http://localhost:8080/api/dev-group/` [GET]
```bash
[
    {
        "code": 7,
        "branchLocation": {
            "code": 2,
            "company": {
                "auto_created_id": 1,
                "name": "sample",
                "created_on": "2022-05-03T14:38:19.256658",
                "updated_on": "2022-05-03T14:38:19.256676"
            },
            "branch_name": "branch field",
            "address": "address field",
            "created_on": "2022-05-03T14:38:44.692117",
            "updated_on": "2022-05-03T14:38:44.692132"
        },
        "group_name": "group name",
        "created_on": "2022-05-03T20:41:12.586829",
        "updated_on": "2022-05-03T20:41:12.586842"
    },
    {
        "code": 11,
        "branchLocation": {
            "code": 2,
            "company": {
                "auto_created_id": 1,
                "name": "sample",
                "created_on": "2022-05-03T14:38:19.256658",
                "updated_on": "2022-05-03T14:38:19.256676"
            },
            "branch_name": "branch field",
            "address": "address field",
            "created_on": "2022-05-03T14:38:44.692117",
            "updated_on": "2022-05-03T14:38:44.692132"
        },
        "group_name": "group name1",
        "created_on": "2022-05-03T20:41:12.586849",
        "updated_on": "2022-05-03T20:41:12.586851"
    },
    {
        "code": 13,
        "branchLocation": {
            "code": 2,
            "company": {
                "auto_created_id": 1,
                "name": "sample",
                "created_on": "2022-05-03T14:38:19.256658",
                "updated_on": "2022-05-03T14:38:19.256676"
            },
            "branch_name": "branch field",
            "address": "address field",
            "created_on": "2022-05-03T14:38:44.692117",
            "updated_on": "2022-05-03T14:38:44.692132"
        },
        "group_name": "group name2",
        "created_on": "2022-05-03T20:41:12.586855",
        "updated_on": "2022-05-03T20:41:12.586857"
    }
]
```

- `http://localhost:8080/api/dev-group/{group_code}` [Delete]
```bash
no Contents
```

## 특이사항
- 필요에 따라 update를 구현할 예정
- 추후 device 관련 로직 필요
