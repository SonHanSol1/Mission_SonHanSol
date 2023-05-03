## Title: [3Week] 손한솔

### 미션 요구사항 분석 & 체크리스트

---
#### 필수미션 - 네이버 클라우드 플랫폼을 통한 배포(도메인 없이, IP로 접속)
#### 배경
- 네이버클라우드플랫폼을 이용합니다
- 강사의 가이드영상대로 진행하시면 됩니다.
- 나머지 미션을 수행하신 후 마지막에 진행하시면 됩니다.
#### 목표
- [ ] https://서버IP:포트/ 형태로 접속이 가능
- [ ] 운영서버에서는 각종 소셜로그인, 인스타 아이디 연결이 안되어도 됩니다.
#### 필수미션 - 호감표시/호감사유변경 후, 개별 호감표시건에 대해서, 3시간 동안은 호감취소와 호감사유변경을 할 수 없도록 작업
#### 배경
- 현재 UI에서는 이 요구사항에 대한 작업이 완료되었습니다.
- 백엔드 쪽에서 체크하는 로직만 추가하면 됩니다.
#### 목표
- [ ] 호감표시를 한 후 개별호감표시건에 대해서, 3시간 동안은 호감취소와 호감사유변경을 할 수 없도록 작업
- [x] 호감사유변경을 한 후 개별호감표시건에 대해서, 3시간 동안은 호감취소와 호감사유변경을 할 수 없도록 작업
#### 선택미션 - 알림기능 구현
#### 배경
- 현재 알림페이지의 UI 레이아웃은 구현이 된 상태입니다.
- 이를 기반으로 나머지 구현을 이어나가시면 됩니다.
- 페이징 처리는 하지 않아도 됩니다.
#### 목표
- [ ] 호감표시를 받았거나, 본인에 대한 호감사유가 변경된 경우에 알림페이지에서 확인이 가능하도록 해주세요. 
- [ ] 각각의 알림은 생성시에 readDate 가 null 이고, 사용자가 알림을 읽으면 readDate 가 현재날짜 로 세팅되어야 합니다.


### 3주차 미션 요약

---

**[접근 방법]**
- 강사님 강의 영상 참조
- 초 단위로 계산 후에 시간, 분으로 변경

**[특이사항]**
- UI에 쿨타임 남은 시간 밖에 하지 못함
- 쿨타임 설정에 관한 부분을 이해 했으나 구현하지 못함
- 그로 인해 배포까지 진행하지 못했다
- 따로 더 진행해서 마무리를 해야겠다.