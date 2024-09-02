# RxRockPaperScissors
RxRockPaperScissors

[ 클라우드 Rx (<a href='https://rxapis.com'>https://rxapis.com</a>) ]에서 제공합니다.
* 해당 연도 말까지 테스트 가능합니다.

## Table of Contents

- [Rx Brain Node](#rx-brain-node)
- [RockPaperScissors](#RockPaperScissors)
- [RxPersonalityIndicator](#RxPersonalityIndicator)



## Rx Brain Node
Visit https://github.com/search27/rxbrains


## RockPaperScissors
* 가위바위보 기본 게임 동작 프로그램

```javascript
const defaultRule = [
    { input: [1, 0, 0, 1, 0, 0], output: [0, 0, 1] },
    { input: [0, 1, 0, 0, 1, 0], output: [0, 0, 1] },
    { input: [0, 0, 1, 0, 0, 1], output: [0, 0, 1] },

    { input: [1, 0, 0, 0, 1, 0], output: [0, 1, 0] },
    { input: [1, 0, 0, 0, 0, 1], output: [1, 0, 0] },

    { input: [0, 1, 0, 1, 0, 0], output: [1, 0, 0] },
    { input: [0, 1, 0, 0, 0, 1], output: [0, 1, 0] },

    { input: [0, 0, 1, 1, 0, 0], output: [0, 1, 0] },
    { input: [0, 0, 1, 0, 1, 0], output: [1, 0, 0] },
];

window.gameData = {
    round : 0, aiScore : 0, humanScore : 0, winner : -1,
    time : 0, trickCount : 0,
}
```

```javascript
const prg = new RxFramework.RxRockPaperScissors({
    target : document.getElementById('targetDom'),      // Target Element For Display Program
    HumanChoose : HumanChoose,                          // Human Choose
});

// Random Choose
const randomChoose = [[1, 0, 0], [0, 1, 0], [0, 0, 1]];
prg.SetDecision(randomChoose[Math.round(Math.random() * (randomChoose.length - 1))]);

// 가위바위보 - 선택
const HumanChoose = (_result) => {
    const winner = prg.CheckWinner(_result, defaultRule);
    prg.AppendScore(winner, gameData);
    prg.ClearDecision();
}

```


## RxPersonalityIndicator
* MBTI 기본 질문

### 생성
```javascript
    personality = new RxFramework.RxPersonalityIndicator();
    const msg = `MBTI 질문 테스트입니다.`;
    personality.AskProceedings(msg, personality.GetRandomAsk);
```
```javascript
    personality.GetRandomAsk();                     // 랜덤 질문 생성
    const result1 = personality.GetMbtiPoints();     // 해당 점수 반환
    const result2 = personality.GetMbtiAskCount();   // 질문 횟수 반환
    const result3 = personality.GetMbtiState();      // 결과 값
```


