# Leture 3, Leture 4
## Q 러닝 개요
### Q 러닝 <br>
모델없이 학습하는 강화학습 알고리즘
목표: 에이전트가 특정 상황에서 특정 행동을 하라는 최적의 정책을 배우는 것으로, 현재 상태로부터 시작하여 모든 연속적인 단계들을 거쳤을 때 전체 보상의 예측값을 극대화

### Q value <br>
- 어떤 상태 s에서 어떤 행동 a를 했을 때, 그 행동의 가치를 나타내는 Q(s,a) 함수를 사용
- 미래의 보상을 계산하기 위해 0~1 사이의 γ(Discount Factor)를 사용
- 현재 상태로 부터 Δt 시간이 흐른 후에 얻는 보상 r은 𝛾Δ𝑡만큼 할인된 𝑟 ∗ 𝛾Δ𝑡로 계산
- Q value는 어떤 시간 t에 따라 행동 a를 할 때 미래의 보상들의 총합의 기대값
<img width="675" alt="스크린샷 2023-01-13 오전 4 10 04" src="https://user-images.githubusercontent.com/121830114/212159144-a6a48a22-76bd-42b9-a2c9-a05e0636d756.png">

### Q algorithm
알고리즘이 시작되기 전에 Q 함수는 고정된 임의의 값을 갖는다. 그리고 매 time-step(𝑡)마다 Agent는 행동를 선택하게 되고, 보상 를 받으며 새로운 상태로 전이하고, Q 값이 갱신된다. 이 알고리즘의 핵심은 이전의 값과 새로운 정보의 가중합(weighted sum)을 이용하는 Value Iteration Update 기법이다.
<img width="809" alt="스크린샷 2023-01-13 오전 4 22 32" src="https://user-images.githubusercontent.com/121830114/212161598-f9452903-c6e0-469c-9def-4b248075e526.png">

## gym environment에서 Q learning
agent가 action을 취하는 방법
- random한 액션의 취함 -> 목표에 도달할 확률 낮음, 매번 최적화하지 않은 선택을 한다는 문제 가짐
- 어떤 길을 가기 전에, 미리 알아보고 감 예를 들면, 네이버 지도를 살펴보고 길을 나서는 것과 같은 방법(지도: Q) -> Q도 처음에는 목표를 정확하게 알지 못하지만 지도가 업데이트 되면서 궁극적으로 목표에 도달하는 길을 알게 됨

Q에게 줄 정보는 현재 state와 어떤 action을 선택했는지에 대한 정보다. <br>
그러면 Q는 그 길로 가는 행동이 얼마나 좋은지 알려준다(reward) -> Q function <br>
- 현재 상태에서 취할수 있는 action(Left, Right, Up, Down)에 대한 피드백의 예시
<img width="382" alt="스크린샷 2023-01-13 오전 4 42 42" src="https://user-images.githubusercontent.com/121830114/212166137-41f7b64e-ba40-4f19-8f99-3f2c7bd53980.png">

