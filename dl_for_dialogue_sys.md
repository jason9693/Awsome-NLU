# Deep Learning For Dialogue System



## 현재 CUI ( Conversational UI )의 챌린지

1. 자연어에서의 variability
2. Robustness
3. Recall / Precision의 Trade Off 
   1. cf.) F1 score
4. Meaning Representation
5. 학습 가능성
6. 명료성



## Task Oriented Dialogue System

![](source/tos.jpeg)

1. LU (Language Understanding) : 문장의 의미를 찾는 과정. 크게 DI ( Domain Indentification ), UID ( User Intent Detection ), SF ( Slot Filling 으로 나뉜다. )

   1. DI

   2. UID

   3. SF

      

2. DM ( Dialogue Management ) : LU를 통해 나왔던 slot들을 통해 의사를 결정하고 이전까지의 결정들을 트래킹하는 역할을 한다.

   1. MDP ( Makarov Decision Process ) : 

3. NLG ( Natural Language Generation ) : 사용자가 이해하기 위한 언어를 생성하는 과정. 크게 아래와 같은 두가지의 접근방식이 있다.

   1. 템플릿이나, 룰을 활용하여 텍스트를 생성하는데에 집중한 접근.
   2. corpus기반의 확률론적인 테크닉을 활용한 접근.
      1. 장점
         1. expert한 도메인의 언어에서 실질적인 이득을 본다.
         2. 분류나 라벨링 에서 생긴 문제를 갱신한다.



## Deep Learning Based Dialogue System

### Language Understanding

* DBN, DNN -> DI와 UID에 사용.
* RNN : Slot Filling에 있어서, 딥러닝을 **Feature Generator** 관점으로 바라본다. 그리고 뉴럴넷 구조를 [CRF](https://ko.wikipedia.org/wiki/%EC%A1%B0%EA%B1%B4%EB%B6%80_%EB%AC%B4%EC%9E%91%EC%9C%84%EC%9E%A5) 와 함께 merge한다. 이후 Slot Filling을 위해 RNN을 Sequence Labelling에 사용한다. 이러한 구조는 나중에 여러 도메인에서 Slot Filling과 Intent Detection에 동시에 사용되는 구조로 확장된다. 
* cf) Bio 태깅
* E2E의 메모리 네트워크는 상대적으로 긴 term의 knowledge context와 짧은 term의 dialogue context를 intergrate하는데에 좋은 메커니즘을 가짐을 증명하였댜. 

### Dialogue Management

* 현재 DM의 SOTA는 dialog상태를 neural로 트래킹 하는 방식에 포커스 되어있다. 초기 모델들 중 하나는 RNN베이스의 state-tracking 접근방식인데, bayesian보다 더 나은 성능을 보였다.
* 더 최신버전인 **Neural Dialog Managers**는 **[knowledge graph](https://psyhm.tistory.com/35) representation** 같이 utterence들 사이의 slot-value pair로 이루어진 conjoint representation을 제공하는데, neural dialog 모델이 현재의 dialogue 시스템에서 더 큰 도메인을 deploying 하고자 할때 생기는 문제점을 극복할 수 있음이 증명되었다.

### Natural Language Generation

* RNN베이스의 NLG는 unaigned된 데이터를 sentence planning과 surface realization으로 동시에 optimizing 하는것으로 학습이 가능하다. 그리고 또한, language variation(언어 변이) 을  output의 후보들중에 샘플링하는 기법을 사용하여 쉽게 처리할수 있다.
* 더 나아가, nl을 생성하는 동안, 의미 반복을 방지하기 위해 사용되는 dialgue act를 제어하기 위한 gating 메커니즘을 사전 작업으로 추가하는것으로 더 나은 성능을 보인다. 



