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

3. NLG ( Natural Language Generation ) : 사용자가 이해하기 위한 언어를 생성하는 과정. 크게 아래와 같은 두가지의 접근방식이 있다.

   1. 템플릿이나, 룰을 활용하여 텍스트를 생성하는데에 집중한 접근.
   2. corpus기반의 확률론적인 테크닉을 활용한 접근.
      1. 장점
         1. expert한 도메인의 언어에서 실질적인 이득을 본다.
         2. 분류나 라벨링 에서 생긴 문제를 갱신한다.