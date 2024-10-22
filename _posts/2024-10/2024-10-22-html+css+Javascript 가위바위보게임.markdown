---
title: TIL(20241022) [html+css+Javascript 가위바위보게임]
author: hanni
date: 2024-10-22 11:13:00 +0800
categories: TIL
tags: [Html, Css, Javascript]
---

----------------------------------------------------------------------------

html+css+javascript로 간단하게 가위바위보게임을 만들었다. <br>

디자인 참고는 [가위바위보게임](https://brendan-fisher.github.io/rock_paper_scissors/)

기초설계라고 하면 조금 우습지만.. 유저가 가위/바위/보 중에 해당하는 이미지를 클릭하면 컴퓨터와 비교<br>
이기면 테이블에서 1점이 올라가는 형식, 그리고 유저와 컴퓨터가 어떤 것을 선택했는지 나오게 하는 것이 목표였다.

```javascript
// html body
<body>

  <nav class="navbar navbar-expand-lg navbar-light bg-light mb-4">
    <div class="container justify-content-center">
      <h1 class="navbar-brand">가위바위보 게임</h1>
    </div>
  </nav>

  <div class="table-responsive mb-4">
    <table class="table table-bordered text-center">
      <thead>
        <tr>
          <th>USER</th>
          <th>COMPUTER</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td id="user-score" class="score">0</td>
          <td id="computer-score" class="score">0</td>
        </tr>
      </tbody>
    </table>
  </div>

  <div class="container text-center">
    <div id="result" class="result alert alert-info" role="alert">
        <div class="d-flex justify-content-center align-items-center">
            <div class="mr-4 d-flex align-items-center">
                <p id="user-choice-text" class="mb-0">USER:</p>
                <img id="user-choice-img" src="" alt="User Choice" class="result-img ml-2" style="display: none;" />
            </div>
            <div class="d-flex align-items-center">
                <p id="computer-choice-text" class="mb-0">COMPUTER:</p>
                <img id="computer-choice-img" src="" alt="Computer Choice" class="result-img ml-2" style="display: none;" />
            </div>
        </div>
        <p id="result-text"></p>
        <p id="win-rate"></p>
    </div>
</div>

  <div class="container text-center">
    <div id="game-container" class="d-flex justify-content-center mb-4">
      <div class="hand mx-2" id="rock" onclick="play('rock')">
        <img src="images/rock.png" alt="Rock" width="150" height="120" />
      </div>
      <div class="hand mx-2" id="paper" onclick="play('paper')">
        <img src="images/paper.png" alt="Paper" width="150" height="120" />
      </div>
      <div class="hand mx-2" id="scissors" onclick="play('scissors')">
        <img src="images/scissors.png" alt="Scissors" width="150" height="120" />
      </div>
    </div>
  </div>
</body>
```

```javascript
// javascript 
let playerScore = 0;
let computerScore = 0;
let totalGames = 0; // 총 게임 수

function play(playerChoice) {
  const choices = ['rock', 'paper', 'scissors']; 
  const computerChoice = choices[Math.floor(Math.random() * 3)]; // 0이상 3미만 숫자 

  // 초기화
  let result = '';
  document.getElementById('result-text').textContent = '';

  // 이미지 업데이트
  const userImage = document.getElementById('user-choice-img');
  const computerImage = document.getElementById('computer-choice-img');
  userImage.src = `images/${playerChoice}.png`;
  computerImage.src = `images/${computerChoice}.png`;

  // 결과 처리
  if (playerChoice === computerChoice) {
    result = '무승부!';
  } else if ( // 유저가 이기는 경우만 
    (playerChoice === 'rock' && computerChoice === 'scissors') ||
    (playerChoice === 'paper' && computerChoice === 'rock') ||
    (playerChoice === 'scissors' && computerChoice === 'paper')
  ) {
    result = '당신이 이겼습니다!';
    playerScore++;
    document.body.classList.add('winner');
    setTimeout(() => document.body.classList.remove('winner'), 1000);
  } else { 
    result = '컴퓨터가 이겼습니다!';
    computerScore++;
    document.body.classList.add('loser');
    setTimeout(() => document.body.classList.remove('loser'), 1000);
  }

  document.getElementById('result-text').textContent = result;
  document.getElementById('user-score').textContent = playerScore;
  document.getElementById('computer-score').textContent = computerScore;

  // 승률 계산 및 표시
  totalGames++;
  const winRate = ((playerScore / totalGames) * 100).toFixed(2); // 유저의 승점/총 게임수 * 100 / 소숫점 2자리 까지만
  document.getElementById('win-rate').textContent = `승률: ${winRate}%`;

  animateHands(playerChoice);
}

function animateHands(playerChoice) {
  const hands = document.querySelectorAll('.hand');
  hands.forEach(hand => {
    hand.style.transform = 'scale(1)';
    hand.style.backgroundColor = '#fff';
  });

  document.getElementById(playerChoice).style.transform = 'scale(1.2)';
}

```

디자인이 뭔가 이쁘진 않은 것 같은데, 처음으로 만들어 본 단순한 게임!

아래는 내가 만든 가위바위보게임 시연영상이다. 


[가위바위보게임 시연영상](https://www.veed.io/view/63f1d711-6c55-4ecd-bff3-b91ef204ac1b?panel=share)