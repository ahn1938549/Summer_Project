# Convolutional neural networks: for sentence classification

## Introduction

-   CNN에 word vector로 방향성과 문법에 따른 의미를 부여함.
-   Max Pooling으로 최대의 학습효과를 기대하였다.
-   굉장히 얕은 Layer로 연산을 최소화 하였으나 좋은 연산능력을 보여주었다.

## Model
- max-over-time pooling operation ( max-pooling)을 사용하여 최대값을 얻은 후
- 하나의 filter에 대하여 하나의 feeature만을 뽑아내(특징) 이를 한 곳에 모아 penultimate layer를 생성 후 이에 따라 
- fully connected softmax layer을 통과하여 값을 얻어낸다.

### Regularization
- 마지막 Layer에서 drop-out과 l2norm 기법을 사용하여 중복된 hidden layer의 문제를 최소화 하였다.
- ![qwq](https://user-images.githubusercontent.com/69898343/133556690-3dc31dec-53e9-462c-bd8a-968c6a0efd81.png)
다음과 같은 기법으로 r이 Bernoulli분포를 따르기 때문에 0 혹은 1의 값을 갖는다.

### Result
![image](https://user-images.githubusercontent.com/69898343/133557331-e901652b-4e90-4b92-818b-77f6401334ff.png)
- Word2vec에서 사전훈련된 단어를 사용할 경우 정확도가 크게 증간한다.
- rand는 그대로 vector적용 X
- static은 word2vec 사전훈련
- non-static은 사전훈련과 동시에 역전파로 계속 vector들이 수정되어 진 학습모델



### 고찰
- 기존 one-hot 벡터로 단어를 표현하는 점에서 벗어나, 단어들끼리의 결합관계를 생성하고 이에 따라 알고리즘이 자동으로 대안의 단어를 학습할 수 있다는 점이 놀라웠다.
![image](https://user-images.githubusercontent.com/69898343/133558199-b43668c8-2bfa-4805-ba42-fbbd75890255.png)
과 같이 non-static이 조금 더 단어에 대하여 연관성을 잘 표시하는 점을 알 수 있었다.
