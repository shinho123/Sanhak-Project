# 2022-1-Sanhak-Project
2022년도 1학기 산학프로젝트
# 산학 프로젝트 플레도 AI 학습블록


## 데이터 소개 
- **사용 데이터** : 플레도 AI 학습블록 사용 로그 데이터
  - 총 데이터 수 : 63,366
  - 유저 수 : 105명
  - Feature 종류 : 아이 고유 식별값, 아이 생년월일, 아이 성별, 단계, 컨텐츠 분류1, 컨텐츠 분류2, 컨텐츠 분류3, 단계, 단계별 문제, 문제 세부 번호, 문제 고유 식별 값, 학습 시각, 문제풀이 소요시간, 문제 정답, 아이 블록 입력 데이터, 정오답, 통계 메인 키, 향상 능력
 
- **같은 유저가 같은 문제에 대한 로그가 중복으로 쌓일 경우 하나로 COUNT**
  - 컨텐츠 분류 중 요리, 음악, 미술의 경우는 정오답이 아닌 과정이 로그 데이터로 쌓임
  - 컨텐츠 분류 중 한글, 수학, 영어의 경우 여러 번 오답을 제출한 뒤 정답에 도달하는 경우
 
- **문제풀이 소요시간은 전체 데이터(로그)를 살리고 3가지 분류별로 나이, 성별에 따라 EDA를 진행함**
  - 컨텐츠, 향상능력, 문제풀이 소요시간 → 나이, 성별에 따라 EDA 진행
    
![image](https://github.com/shinho123/2022-1-Sanhak-Project/assets/105840783/5bee1196-8826-401c-be0c-393c394eef55)

## EDA
- EDA는 나이, 성별, 이상치 순으로 나누어 분석함
  - **나이** : 나이별 컨텐츠 분류, 나이별 향상능력 분류, 나이별 문제풀이 소요시간
  - **성별** : 성별별 컨텐츠 분류, 성별별 향상능력
  - **이상치 확인 및 제거** : 각 컨텐츠 별로 이상치를 확인함(Q1-(1.5*IQR)미만, Q3+(1.5*IQR) 초과인 값을 제거함)
 
## Analysis
나이·성별
<img width="612" alt="image" src="https://github.com/shinho123/2022-1-Sanhak-Project/assets/105840783/56295fc1-4a26-4831-a9b2-3791a6084c04">

- 105명 → 96명(10세 보다 나이가 많은 유저는 제외시킴)
- 5~7세의 유아가 가장 많이 이용함
  - 유아의 경우 1살 차이도 발달 능력에서 큰 차이를 보임
- 남자 : 51명, 여자 : 45명으로 남녀의 비율 차이가 없음

- 컨텐츠 분류
<img width="248" alt="image" src="https://github.com/shinho123/2022-1-Sanhak-Project/assets/105840783/fee9a7fe-a701-445e-a1c8-7b38b10a8d87">

- 한국 교육의 학업별 중요도에 따라 국어, 수학, 영어의 이용이 많을 것으로 예상되었음
- 결과적으로 주요 과목인 국어, 수학, 영어가 가장 많은 이용량을 보이고 있음
- 예체능 계열에서는 미술 영역이 가장 많은 이용량을 보였음
- 결론적으로 아이 학습에 국어, 영어, 수학에 비중을 많이 두고 교육하는 것을 알 수 있음


  
  



   
## 신규 서비스 시나리오 제안
- 인터페이스 제공
  - User의 나이, 성별에 따른 평균 컨텐츠 진도 수준, 향상능력 수준 등을 그래프로 시각화
  - 각 문제에 따른 평균 문제풀이 소요시간 제공
    - 사용 데이터 : 전체 유저의 문제풀이 소요시간, 컨텐츠 선택 수, 향상능력 수
- 고객 이탈률 방지 서비스
  - 일정기간 접속하지 않은 고객에게 알람 서비스
    - 사용 데이터 : User의 학습 시각, 로그데이터
- 오답노트 서비스
  - 자주 틀린 문제를 다시 점검하여 반복학습이 가능하도록 하는 서비스
    - 사용 데이터 : User의 정오답, User 블록 입력 데이터
