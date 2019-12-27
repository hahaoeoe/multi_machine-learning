# 나이브 베이즈 (Naive Bayes Classification)

## 개요

> 설명변수(독립변수, 특성;*Feature*)
>
> 목적변수(반응변수, 종속변수, 목표변수, 출력값)

베이즈 정리에 근거하여, 목적변수가 발생할 조건부확률을 사전확률과 우도 함수의 곱으로 표현하여 어떤 분류항목에 속할지 확률이 높게 계산되는 쪽으로 분류하는 기법. 이때 모든 관측값은 서로 다른 관측값과 통계적으로 독립적으로 발생한다고 가정 (별다른 확신 없이 가정하므로 Naive 모형이라고 부름)



## 기초개념

나이브 베이즈 기법을 적용하기 위해서는 베이즈의 정리(Bayes' theorem)와 사후확률의 개념을 이해할 필요가 있다. 베이즈 정리는 조건부 확률을 계산하는 방법 중 하나이다. 



#### 1. 조건부 확률 (conditional probability)

##### 1.1 정의

확률 공간에 A,B라는 사건이 있을 때

1) A사건이 발생했을 때, B사건이 일어날 확률

![img](https://t1.daumcdn.net/cfile/tistory/998397385C0930C125)



2) B사건이 발생했을 때, A사건이 일어날 확률

![img](https://t1.daumcdn.net/cfile/tistory/999D963B5C09307125)



위의 두 식에 간단한 곱셈을 적용하여 우리는 아래의 식을 유추해 낼 수 있다. 

####                                                      **P(A∩B) = P(A|B)P(B) = P(B|A)P(A)**





##### 1.2 독립사건에서의 조건부 확률

: A, B 사건이 서로 독립일 때, A와 B가 동시에 일어날 확률

####                                       **P(A∩B)=P(A)×P(B)**



: 사건이 독립이라면, 다음의 수식을 항상 만족하게 된다.

<img src="https://t1.daumcdn.net/cfile/tistory/995F32445B721F0D43" alt="img" style="zoom:150%;" />





#### 2. 베이즈 정리(**Bayes' theorem**) 

> 용어 파악
>
> * 사전확률(Prior Probability)
>
>   * 이미 알고 있는 사건(들) 확률
>
>   - 새로운 정보가 들어오기 이전까지의 확률을 말한다. 즉 조건부 확률이 없는, 조건부가 들어오기 이전의 확률을 의미한다.
>
> * 우도(Likelihood Probability)
>
>   * 이미 알고 있는 사건(들)이 발생했다는 조건하에, 다른 사건이 발생할 확률
>   * 베이즈 정리에서는 P(B|An)을 의미
>   * 최대우도 : 각 관측값에 대한 총 우도의 최대가 되게 하는 분포
>
> * 사후확률(Posterior probability)
>
>   * 사전확률과, 우도확률을 통해서 알게되는 조건부 확률
>   * 새로운 정보가 들어온 이후의 확률을 말한다. 조건부 확률에서의 조건 확률이 공급된 후의 사후확률이다.
>   * 사건 발생 후에 어떤 원인으로부터 일어난 것이라고 생각되어지는 확률 또는 추가된 정보로부터 사전정보를 새롭게 수정한 확률



##### 2-1. 정의

* 베이즈 정리(Bayes' theorem, bayes'rule)는 이전의 경험과 현재의 증거를 토대로 어떤 사건의 확률을 추론하는 과정
* 추론 대상의 사전 확률과 추가적인 정보를 기반으로 해당 대상의 사후 확률을 추론하는 통계적 방법을 베이즈 추정(Bayesian Estimation)
* 쉽게 말해서, 내가 발생확률을 아는 사건(사전확률), 그 사건이 발생했다는 조건하에서의 다른 사건의 발생확률(우도)을 안다면, 다른 사건이 발생했다는 조건하에서의 내가 발생확률을 아는 사건의 발생확률을 계산할 수 있다는 것



베이즈 정리는 아래와 같다. 확률의 곱셈공식과 전체확률의 법칙에 대한 공식을 기반으로, 약간의 수식적인 테크닉들만을 이용하여 조건이 주어졌을 때 특정한 확률을 구해내는 것을 의미한다.

![img](https://t1.daumcdn.net/cfile/tistory/9933A64A5B72255121)







![img](https://t1.daumcdn.net/cfile/tistory/99ADEB405C0BC79008)







## 나이브 베이즈(Naive Bayes Classification)





~~~R
## 나이브 베이즈 예습

data(iris)
library(caret)

# 150건 --> 70% (105건 ==> 3)

idx <- createDataPartition(iris$Species, p=0.7,list=F)

# 70%로 학습용 데이터 셋트 추출
iris_train <- iris[idx,]

iris_test <- iris[-idx,]

table(iris_train$Species)
table(iris_test$Species)

library(e1071)

naive.result <- naiveBayes(iris_train, iris_train$Species, laplace = 1)

# 나이브 베이즈 적합
naive.pred <- predict(naive.result, iris_test, type="class") # 데이터 데이터 평가
table(naive.pred, iris_test$Species) # 분류 결과 도출

confusionMatrix(naive.pred,iris_test$Species)

# 확률을 이용해서 구하는 것 




## 선생님 예제 나이브 베이즈 풀기

 # 문제 1
getwd()
setwd("C:\\rwork\\MLData")

movie <- read.csv("movie.csv", header = T)
library(e1071)
nm <- naiveBayes(movie[1:5], movie$장르, laplace = 0)
head(movie)

result <- predict(nm, movie[1:5])
sum(movie$장르 != result)

result


 # 문제 2
mail <- read.csv("spam.csv", header = T)
mail[is.na(mail)] <- 0
nm2 <- naiveBayes(mail[2:13], mail$메일종류, laplace = 0)
head(mail)

result2 <- predict(nm2, mail[2:13])
sum(mail$메일종류 != result2)
result2
nm2




## 인공신경망 예제

library(nnet) # 인공 신경망 기법을 사용하기 위한 nnet 패키지 로딩 / 다층 퍼셉트론
 # nnet은 노드 수 늘려주는 함수 (중간층 1개를 기준으로)
iris_train_scale <- as.data.frame(sapply(iris_train[,-5],scale))
iris_test_scale <- as.data.frame(sapply(iris_test[,-5],scale))
iris_train_scale$Species <- iris_train$Species
iris_test_scale$Species <- iris_test$Species

nnet.result <- nnet(Species~., iris_train_scale, size=3)

 # 훈련데이터 통한 모형 적합
nnet.pred <- predict(nnet.result, iris_test_scale, type ="class") #테스트 데이터 평가

table(nnet.pred, iris_test$Species)
~~~











