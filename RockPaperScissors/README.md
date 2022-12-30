## iOS 커리어 스타터 캠프

### 프로젝트 설명
1. 제목: 묵찌빠게임

2. 소개: 1~3사이의 숫자를 전달받아, 컴퓨터의 1~3 사이의 랜덤한 숫자와 가위바위보로 승패를 결정후, 묵찌빠로 다시 승패를 결정하는 게임

3. 팀원
- 닉네임 : goat, kokkilE
- 미모지 : 
<img src="https://i.imgur.com/6TT1qhx.png" width="100" height="100"/> <img src="https://i.imgur.com/4I8bNFT.png" width="100" height="100"/>


- 역할 : 커밋별로 드라이버 1명과 네비게이터 1명으로 번갈아가며 진행
    
4. 타임라인: 시간 순으로 프로젝트의 주요 진행 척도를 표시
- 12/26 (월) : STEP 0
- 12/27 (화) : STEP 2까지 진행 완료 (STEP 1 Review 대기중)
- 12/28 (수) : STEP 2 진행완료 및 pr
- 12/29 (목) : STEP 1 리뷰를 반영해서 수정 및 STEP 2 PR 완료
- 12/30 (금) : STEP 2 리뷰를 반영해서 수정 진행 중

5. 시각화된 프로젝트 구조 <br/>

<details>
<summary>순서도</summary> :fire: 
<div markdown="1">

![](https://i.imgur.com/CxQAgiO.jpg)
    
</div>
</details>


6. 실행 화면(기능 설명)
- 가위바위보 입력 화면 및 입력 오류 처리
![](https://i.imgur.com/ShpeqCl.png)

- 묵찌빠 입력 화면 및 입력 오류 처리
![](https://i.imgur.com/sZHTSgy.png)

- 게임종료[0]
![](https://i.imgur.com/FnkxLUZ.png)

7. 트러블 슈팅
 
- 가위바위보의 승무패를 확인하는 로직
startRockPaperScissors() 함수와 startMukChiBa() 함수를 별도로 구현할지, 하나의 함수로 구현할지 고민이 되었다.
기본적으로 가위바위보와 묵찌빠의 동작은 상당히 유사하고, 차이가 있는 부분은 switch-case 구문 내 동작이었다.
별도의 함수로 구현할 경우 반복되는 코드가 많아지기 때문에 하나의 함수 startGame()으로 구현하였고, currentGame 변수의 열거형 데이터와 현재 게임의 승자값을 튜플로 받아 switch문으로 검사하여 실행되도록 구현했다.

- 전역변수 지양
startGame()내에서 현재의 게임상태와 / 현재의 승자 상태 var = winner: String 라는 전역상수로 값을 받아오던 상태에서 피드백이후, 따로 nameSpace화 해주어 열거체안에 넣어 해결하는 방식으로 진행했다.

- Github 충돌
우리는 **3조 브랜치 (Step 1)** 이 merge되지 않은 시점에서 **3조 브랜치 (Step 2)** 를 생성해서 Step 2를 먼저 진행했다. 그 이후 **3조 브랜치 (Step 2)** 를 원본 저장소의 **3조 브랜치** 에 PR을 보낼 때 충돌이 발생했다.
<img src="https://i.imgur.com/jRCdYjl.png" width="550" height="450"/>
우리가 충돌의 원인을 **3조 브랜치 (Step 2)** 의 커밋 이력에 **커밋 #1-4** 이 누락되어있기 때문이라고 생각했다. 커밋 #1-3 이후 커밋이 두갈래로 갈라졌기 때문이다.
**3조 브랜치 (Step 2)** 와 **3조 브랜치 (Step 1)** 을 merge한 후 다시 커밋을 하니 충돌이 해결되었다.
``` swift
git switch 3조 브랜치 (Step 2)    // 3조 브랜치 (Step 2)로 이동
git merge 3조 브랜치 (Step 1)    // 3조 브랜치 (Step 2)에 3조 브랜치 (Step 1)를 병합
git commit
git push
```

8. 참고 링크
- [GitHub Docs - Resolve merge conflicts](https://docs.github.com/ko/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-on-github)
- [API Design Guidelines](https://www.swift.org/documentation/api-design-guidelines/)

9. 팀회고
/Users/songjonghwan/Desktop/StarterCamp/ios-rock-paper-scissors/팀회고.md
