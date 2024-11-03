# java-lotto-precourse

### 1. 사용자 입력 기능
**로또 구입 금액 입력**:사용자가 로또를 구매할 금액을 입력
- **제약 사항**: 금액은 1,000원 단위로 입력
- **예외 처리**: 
  － 입력된 금액이 숫자가 아닌 경우 IllegalArgumentException 발생 후, "[ERROR] 구입 금액은 숫자여야 합니다." 메시지 출력
  － 입력된 금액이 1,000원으로 나누어 떨어지지 않으면 IllegalArgumentException을 발생 후, "[ERROR] 구입 금액은 1,000원 단위여야 합니다."라는 메시지를 출력
  
**당첨 번호 입력**: 사용자가 추첨할 당첨 번호 6개를 쉼표(,)로 구분하여 입력
- **제약 사항**: 각 번호는 1부터 45 사이의 숫자, 중복 불가
- **예외 처리**: 
  - 숫자가 6개가 아닌 경우 IllegalArgumentException을 발생 후, "[ERROR] 당첨 번호는 6개여야 합니다." 메시지 출력
  － 입력된 번호가 1~45 범위를 벗어나거나 중복되는 경우 IllegalArgumentException을 발생시키고 "[ERROR] 로또 번호는 1부터 45 사이의 숫자여야 하며 중복되지 않아야 합니다."라는 메시지를 출력한다.

**보너스 번호 입력**: 당첨 보너스 번호 1개를 입력
- **제약 사항**: 보너스 번호는 1부터 45 사이의 숫자, 당첨 번호와 중복되지 않아야 한다.
- **예외 처리**: 
  - 보너스 번호가 1~45 범위를 벗어나거나 당첨 번호에 포함된 경우 IllegalArgumentException을 발생 후, "[ERROR] 보너스 번호는 1부터 45 사이의 숫자여야 하며 당첨 번호와 중복되지 않아야 합니다." 메시지 출력
  - 숫자가 1개가 아닌 경우 IllegalArgumentException을 발생 후, "[ERROR] 보너스 번호는 1개여야 합니다." 메시지 출력

### 2. 로또 번호 발행 기능
- **발행 기준**: 로또 한 장의 가격은 1,000원, 입력받은 금액에 따라 발행할 로또의 수 계산
Randoms.pickUniqueNumbersInRange(1, 45, 6) 메서드를 사용하여 1부터 45 사이의 중복되지 않는 6개의 숫자를 랜덤으로 생성
- **출력 형식**: 각 로또 번호는 오름차순으로 정렬하여 출력한다.

### 3. 게임 진행 및 결과 계산 기능
- **등수 기준**:
  1등: 6개 번호 일치 (2,000,000,000원)
  2등: 5개 번호 + 보너스 번호 일치 (30,000,000원)
  3등: 5개 번호 일치 (1,500,000원)
  4등: 4개 번호 일치 (50,000원)
  5등: 3개 번호 일치 (5,000원)
- **우승자 결정**:
  - 각 로또의 일치 번호 수와 보너스 번호 일치 여부를 확인 후, 등수 계산
  - 각 등수별 당첨 횟수를 기록, 총 수익률 계산
- **출력 형식**:
  - 당첨 내역 및 각 등수의 당첨 횟수 출력
  - 총 수익률은 소수점 둘째 자리에서 반올림해서 출력

### 4. 예외 처리 및 에러 메시지
- 모든 에러 메시지는 [ERROR]로 시작하며, 적절한 오류 설명 포함
- 예외 발생 시 해당 부분부터 다시 입력
