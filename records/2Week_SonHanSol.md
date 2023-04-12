## Title: [2Week] 손한솔

### 미션 요구사항 분석 & 체크리스트

---
#### 필수미션 - 호감상대 삭제

#### 배경
- 호감상대등록과 호감표시는 동의어입니다.
- 현재 호감표시기능이 구현되어 있고 아래와 같은 예외처리는 이미 구현되어 있습니다.
- 케이스 1 : 현재 로그인을 하지 않으면 호감표시를 할 수 없습니다.
- 케이스 2 : 현재 본인의 인스타ID를 등록하지 않은 회원은 호감표시를 할 수 없습니다.
- 케이스 3 : 현재 본인이 본인의 인스타ID를 호감상대로 등록할 수 없습니다.
#### 목표
- 케이스 4 : 한명의 인스타회원이 다른 인스타회원에게 중복으로 호감표시를 할 수 없습니다. 
  - 예를들어 본인의 인스타ID가 aaaa, 상대의 인스타ID가 bbbb 라고 하자. 
  - aaaa 는 bbbb 에게 호감을 표시한다.(사유 : 외모)
  - 잠시 후 aaaa 는 bbbb 에게 다시 호감을 표시한다.(사유 : 외모)
  - 이 경우에는 처리되면 안된다.(rq.historyBack)
- 케이스 5 : 한명의 인스타회원이 11명 이상의 호감상대를 등록 할 수 없습니다. 
  - 예를들어 본인의 인스타ID가 aaaa 라고 하자. 
  - aaaa 는 bbbb, cccc, dddd, eeee, ffff, gggg, hhhh, iiii, jjjj, kkkk 에 대해서 호감표시를 했다.(사유는 상관없음, aaaa는 현재까지 10명에게 호감표시를 했음)
  - 잠시 후 aaaa 는 llll 에게 호감표시를 한다.(사유는 상관없음)
  - 이 경우에는 처리되면 안된다.(rq.historyBack)
- 케이스 6 : 케이스 4 가 발생했을 때 기존의 사유와 다른 사유로 호감을 표시하는 경우에는 성공으로 처리한다. 
  - 예를들어 본인의 인스타ID가 aaaa, 상대의 인스타ID가 bbbb 라고 하자. 
  - aaaa 는 bbbb 에게 호감을 표시한다.(사유 : 외모)
  - 잠시 후 aaaa 는 bbbb 에게 다시 호감을 표시한다.(사유 : 성격)
  - 이 경우에는 새 호감상대로 등록되지 않고, 기존 호감표시에서 사유만 수정된다. 
  - 외모 => 성격 
  - resultCode=S-2 
  - msg=bbbb 에 대한 호감사유를 외모에서 성격으로 변경합니다.
### 케이스 4 SQL
``` sql
# 어떠한 회원이 특정회원에 대해서 이미 호감표시를 했는지 검사하는 SQL, 질의결과가 하나라도 있다면 이미 호감을 표시한 경우이다.
# 여기서 1은 로그인한 회원의 인스트 계정 번호이고
# 여기서 2는 상대방의 인스타계정 번호이다.
SELECT *
FROM likeable_person
WHERE from_insta_member_id = 1
AND to_insta_member_id = 2;
```
### 케이스 5 SQL
``` sql
# 어떠한 회원이 호감표시를 총 몇번 했는지 검사하는 SQL
# 여기서 1은 로그인한 회원의 인스타계정 번호이다.
SELECT COUNT(*)
FROM likeable_person
WHERE from_insta_member_id = 1;
```
### 케이스 5 JAVA
``` java
// 내가 좋아하는 사람 리스트
List<LikeablePerson> fromLikeablePeople = rq.getMember().getInstaMember().getFromLikeablePeople();

// 나를 좋아하는 사람 리스트
List<LikeablePerson> toLikeablePeople = rq.getMember().getInstaMember().getToLikeablePeople();
```
### 케이스 6 SQL
``` sql
# 사용자는 호감표시를 했지만 케이스 6에 해당되기 때문에 실제로는 수정이 일어난다.
# 여기서 5는 기존 호감표시 번호이다.
UPDATE likeable_person
SET modify_date = NOW(),
attractive_type_code = 2
WHERE id = 5;
```

### 2주차 미션 요약

---

**[접근 방법]**



**[특이사항]**
