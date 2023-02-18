# DL
All of my Deep Learning Projects Repository






# RNN
RNN - Sequence data를 다루는 모델 : t 시점의 데이터와 t+1 데이터가 연결되고 t+2 데이터가 연결 되는 데이터

Sequence Modeling 의 필요성 : 각기 다른 데이터의 입력과 출력이 필요할 때

#### RNN 의 원리
* 목적 함수 h(t) 를 학습 
* 목적 함수에는 h(t-1)과 x(t) 가 존재 (이전 데이터 결과와 현재 데이터를 이용해 h(t) 학습) 

#### RNN의 단점
* Vanishing and exploding Gradient - 긴 sequence의 경우 영향력이 사라짐
* 많은 시간이 걸림

### RNN VS CNN
* RNN
    * 입력데이터가 순차적 패턴에 의존적일 때 
    * 이전 입력과 다음 입력과 상관 관계가 있을 때
    * 마지막 출력 기반으로 편향(Bias)을 설정
* CNN
    * 모든 데이터는 독립
    * 이전 데이터 기록을 기억하지 못한다.



* one to one
* one to many : 입력은 하나, 여러가지의 시퀀스 출력 (ex. 이미지를 통한 캡션)
* many to one
* many to many

### LSTM

RNN의 vanishing gradient 문제를 해결하기 위해 나온 아키텍쳐

구성요소
* input gate (새로 가져와야하는 데이터)
* memory cell input (마지막 셀에서 나온 데이터)
* forget gate (정보를 분석해 필요하지 않은 정보 잊어버리게 함)
* output gate (출력)
* memory cell ouput (메모리 출력)


1. forget gate (h(t-1)과 x(t) 를 이용해 sigmoid 활성화 함수를 통해 중요하지 않은 정보 잊어버림)
2. input gate ( Cell State - tanh를 이용해 전달 / Input State - sigmoid를 이용해 전달)
3. Current State ( Global Context 유지 )
4. Output Layer (Local Context - x(t) 데이터에 의한 정보 출력) 

### Transformer

어텐션/ 인코더 레이어/ 디코더 레이어로 구성

병렬처리가 힘든 문제를 해결하기 위해

* Self Attention
    * 세개의 벡터 (쿼리 / 키 / 값 ) 사용
    쿼리 : 찾고있는 단어에 관한 것
    키 : 해당 링크
    값 : 최적화된 값

    * Score - 키 / 쿼리의 내적으로 구하는 곱셈
    
    * Divide score - 스코어를 키 벡터 차원으로 나누어 안정적인 그래디언트 얻음
    * Softmax를 통해 확률 찾음
    * 가중치와의 곱을 통한 합을 얻음
