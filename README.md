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
* 54개의 질문 랜덤으로 생성

* Sample
### 생성
```javascript
// 외향형	사교성이 뛰어나 폭 넓은 대인관계를 유지하고 있으며, 활동적인 자리를 조항하고 매사 정렬적이다.
// 내향형	소수와의 깊이 있는 대인관계를 유지하는 것을 좋아하는 편이며, 조용하고 신중하다. 어떤 사건이든 사전에 완벽히 인지한 후의 경험하는 것을 선호한다.
// 사고형	진실과, 사실에 주 관심을 주는 편이며, 논리적 분석적 객관적 판단을 중요하게 생각한다.
// 감정형	사람과 관계를 주로 관심을 두는 편이며, 상황적, 정상을 침작한 설명을 중요시한다.
// 감각형	오감에 의존하는 경향이 있으며 실제 경험을 중요시한다. 현재에 초점을 맞추고 정확하고 철저하게 일처리를 하는 것이 큰 특정이다.
// 직관형	육감 내지 영감에 의존하는 특징을 가지고 있으며, 미래지향적이다. 가능성과 의미 추구, 신속, 비약적으로 일처리를 하는 경향이 있다.
// 판단형	분명한 목적과 방향을 추구하며, 기한 엄수 및 철저한 사전계획을 중점으로 체계적으로 일처리를 하는 것을 선호한다.
// 인식형	목적과 방향을 유동성있게 변화시킬 수 있는 능력이 있으며 자율적이다. 상황에 따라 융통성 있게 일정 변경이 가능하다.

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


