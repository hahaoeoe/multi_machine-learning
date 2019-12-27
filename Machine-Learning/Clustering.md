# 군집화(Clustering) ; 군집분석

군집분석은 데이터들에 존재하는 *유사성 혹은* *비유사성에 근거*하여 패턴화를 하는 특성으로 인해, 주로 유사한 사람들을 그룹화 및 세분화하여 비즈니스에 활용하거나, 유사한 개체들을 묶어 필요한 정보를 압축하여 활용하거나, 유사성 기반의 그룹화를 응용하여 역으로 이상치(outlier) 등의 특이점 혹은 비정상 패턴을 찾는 분야 등에 활용되고 있다.

=>  개체를 분류하기 위한 명확한 분류기준이 존재하지 않거나 기준이 밝혀지지 않은 상태에서 주어진 데이터들의 특성을 고려해 같은 그룹(클러스터)를 정의하고, 다른 클러스터의 개체보다 서로 더 유사한 개체가 되도록 그룹의 대표성을 찾아내는 방법

> ? cluster: 비슷한 특성을 가진 데이터들의 집합



## 군집분석의 목적

유사한 성향을 가진 개체를 모아 군집을 형성하여 군집간의 특성을 관찰하거나 목표변수와의 관계를 파악하기 위함 (예측성 분석이 아니기 때문에 주로 분석 초기 단계에서 데이터의 특성을 파악하기 위해서 활용됨)

---

즉, 비슷한 개체끼리 한 그룹으로, 다른 개체는 다른 그룹이로 묶는 것.

1) 군집 간 분산(inter-cluster variance) 최대화

2) 군집 내 분산(inner-cluster variance) 최소화



 `주의)` 클러스터링은 비지도학습(unsupervised learning)으로, 각 개체의 그룹 정보 없이 비슷한 개체끼리 묶어보는 반면에 정답이 있는 지도학습(supervised learning)인 분류(Classification)는 과제를 수행할 때 데이터의 독립변수(X)로 종속변수(Y)를 예측하도록 학습을 진행한다. 



## 분류(Classification)와 군집화(Clustering)

`클러스터링(Clustering)` 

: 비지도학습(unsupervised learning). 그룹에 대한 정보 없이 비슷한 것끼리 묶는 것

: 데이터 간의 유사도를 정의하고 그 유사도에 가까운 것부터 순서대로 합쳐가는 방법



`분류(Classification)` 

: 지도학습(supervised learning). 데이터마다 레이블이 주어지고 이를 기반으로 학습

: 기존에 존재하는 데이터의 category 관계를 파악하고, 새롭게 관측된 데이터의 category를 스스로 판별하는 과정 



> **차이점** 
>
> 군집은 각 개체의 범주가 군집의 정보를 모를 때, 즉 lable(category)이 없을 때 데이터 자체의 특성에 대해 알고자 하는 목적으로,
>
> 분류는 label(category)이 있을 때, 새로운 데이터의 그룹을 예측하기 위한 목적으로 하는 분석기법이다. 





## 군집 타당성 평가

클러스터링은 정답이 없기 때문에 일반적인 머신러닝 알고리즘처럼 단순정확도(Accuracy) 등 지표로 평가할 수 없다. 이때 군집타당성지표(Clustering Validity Index)를 통해 군집을 만든 결과가 얼마나 유용한지 따질 수 있다. 

* 군집타당성지표(Clustering Validity Index)
  * 군집 간 거리
  * 군집의 지름
  * 군집의 분산  등



## 군집화의 종류 

>Hard clustering: 한 개체가 여러 군집에 속하는 경우를 허용하지 않는 군집화 방법
>
>Soft clustering: 한 개체가 여러 군집에 속할 수 있다.

>**Pational clustering**: 전체 데이터의 영역을 특정 기준에 의해 동시에 구분하는 군집화 방법. 각 개체들은 사전에 정의된 개수의 군집 가운데 하나에 속하게 된다. `K-mean 군집화`가 대표적
>
>**Hierarchical clustering**: 개체들을 가까운 집단부터 차근차근 묶어나가는 방식. 군집화 결과뿐 아니라 유사한 개체들이 결합되는 덴드로그램(Dendrogram)을 생성한다.

> Self-Organizing Map: 뉴럴넷 기반의 군집화 알고리즘
>
> Spectual Clustering: 그래프 기반의 군집화 방법론



![image-20191227170147735](C:\Users\student\AppData\Roaming\Typora\typora-user-images\image-20191227170147735.png)



**1. 분리형(비계층적) 군집화 (Pational clustering)**

: 사전에 군집의 수를 정해주어 대상들이 군집에 할당되로록 하는 것

: 대표적 `K-Means algorithm`



1.1.1 K-평균 클러스터링  개념

* K-평균 클러스터링은 주어진 군집 수 k에 대하여 군집 내 거리 제곱 합의 합을 최소화하는 것을 목적으로 하며, 사전에 결정된(분석가가 결정해야 함) 군집 수 K가 주어지면 데이터 개체 점들 간의 거리를 이용하여 전체 데이터 세트를 상대적으로 유사한 K개의 군집으로 나누게 된다. 
* 노이즈나 이상치에 민감하고, 무작위로 군집 중심점을 할당하는 문제로 인해 전역적 최적해가 아닌, 지역적 최적해에 빠질 우려가 있으며, 연속형 변수를 이용한 거리측도에만 사용 가능하고, 데이터 관측치가 여러 군집 간 중복될 수 있는 경우를 고려할 수 없는 등의 단점을 가지고 있다.
* 중심 기반(Center-based clustering)에 속하며 (프로토타입 기반(Prototype-based)이라고도 한다.) "동일한 군집에 속하는 데이터는 어떠한 중심을 기준으로 분포할 것이다." 라는 가정을 기반으로 한다.



1.1.2 K-Means algorithm 개요

* 대표적인 '분리형 군집화 알고리즘' 가운데 하나로 각 군집은 하나의 중심(centroid)을 가진다. 각 개체는 가장 가까운 중심에 할당되며, 같은 중심에 할당된 개체들이 모여 하나의 군집을 형성한다. 사용자가 사전에 하이퍼파라메터(hyperparameter)인 군집 수(**K**)가 정해야 알고리즘을 실행할 수 있다.

* EM 알고리즘을 기반으로 작동하며 EM 알고리즘은 **Expectation** 스텝과 **Maximization** 스텝으로 이루어져 있다. 해에 수렴할 때까지 (또는 사용자가 지정한 최대 반복횟수 만큼) EM을 반복한다. Expectation 스텝에서는 각 데이터가 어떤 클러스터에 속할지 구하고 데이터는 자기자신으로부터 더 가까운 기준점이 있는 클러스터에 속하게 된다. Maximization 스텝에서는 클러스터의 무게중심으로 기준점을 업데이트한다.  

  



1.1.3  K-Means algorithm 

① K-centroid를 선택한다. 
② 각 데이터 포인트를 가장 가까운 중심(centroid)에 배정한다. 
③ 군집 안에 있는 모든 데이터 포인트의 평균으로 중심을 재계산한다. (즉 중심은 p길이의 평균의 벡터들이고 여기서 p는 변수의 수이다.) 
④ 그들의 가장 가까운 중심에 데이터 포인트를 부여한다. 
⑤ 관측치들이 더 이상 배정되지 않거나 최대 반복 수에 도달할 때까지 단 계 3과 4를 계속한다.



(동일)

① 데이터 준비

② 랜덤으로 기준점을 찍는다. 기준점을 어디에 찍을지, 몇 개를 찍을지는 하이퍼파라미터에 해당

③ **E 스텝** : 각 데이터와 기준점들 사이의 거리를 구해서, 각 데이터가 가장 가까운 기준점에 속하도록 한다. 클러스터 생성됨 

④ **M 스텝** : 각 클러스터 내의 무게중심으로 기준점을 이동

⑤ **E스텝, M스텝을 반복**: 아래 경우 중 하나를 만족할 때까지 

- 해가 수렴하는 경우
- 사용자가 지정한 반복 횟수만큼 반복한 경우



1.1.4 하이퍼파라미터 K 정하기

Elbow method

: 다양한 K의 값을 시도해보고, 값이 현저히 변하는 지점(팔꿈치처럼 꺽이는 지점)이 있는 경우 그 지점을 최적 K값이라 판단한다. 

![img](https://k.kakaocdn.net/dn/pn4Dc/btqwNuRbN8S/GlCS4Y2fWpBTzer1nAkspk/img.png)



팔꿈치(elbow)가 없을 수도 있다. 이때는 클러스터를 나누려는 목적에 따라 정하면 되는데 예를 들어 사람들의 키와 몸무게 데이터가 주어졌을 때, 이 사람들에게 줄 옷을 사이즈별로 제작한다고 가정해본다. 사이즈, 즉 클러스터의 수 K를  옷 사이즈를 3개(S, M, L)로 할지 5개(XS, S, M, L, XL)로 할지는 필요와 목적에 따라 결정한다. 



1.1.5 Goal : 클러스터 내 분산을 최소화하는 클러스터링을 찾는 것

\* 매우 어려운 문제이다. n개의 데이터포인트를 K개의 클러스터로 K^n개의 방법이 있기 때문이다.

\* K-means 알고리즘은 local optimum을 찾아주는 근사 알고리즘 

​     ** local optimum: 더 줄어들 수 없을때 멈추고, 그 점이 local optimum

\* K-means 알고리즘을 여러번해서 서로 다른 결과를 얻었다면?? 클러스터 내 분산이 작은 쪽을 선택한다!

\* EM(Expectation Maximization) 알고리즘의 가장 간단한 형태이다.

>   EM? 관측되지 않는 잠재변수에 의존하는 확률 모델에서 최대가능도(maximum likelihood)나 최대사후확률(maximum a posteriori)을 갖는 매개변수를 찾는 반복적인 알고리즘이다.

\* centroid를 통해 변수의 특징이 아닌 데이터의 특징을 알 수 있다.



~~~ R
result2 <- kmeans(mydia,3) # 군집수 = 3

names(result2) # 컬럼명 뜸 

#군집별 통계
g1 <- subset(mydia, result2$cluster == 1)
summary(g1)
g2 <- subset(mydia, result2$cluster == 2)
summary(g2)
g3 <- subset(mydia, result2$cluster == 3)
summary(g3)
str(mydia)
  
  # g2 > g3 > g1 가격 -> 품질 영향?
  # 그룹 성격을 summary를 토해 해석해볼수 있음
  # result2 에서 betweens 집단 간의 값, withinss는 집단 내의 값

km.out.withness <-c()
km.out.between <- c()

for(i in 2:7){
  set.seed(1)
  km.out <- kmeans(mydia, centers = i)
  km.out.withness[i-1] <- km.out$tot.withinss 
  km.out.between[i-1] <- km.out$betweenss
}
data.frame(km.out.withness, km.out.between)
~~~







**2. 계층적 군집화 (Hierarchical clustering)**

: 각 개체가 n개(객체의 수)의 독립적인 각각의 군집에서 출발하여 점차 거리가 가까운 대상과 군집을 이루어 가는 것

: 각 관측치는 자신을 하나의 최초 군집으로 시작한다. 그 다음 유사도를 이용해 한번에 두 개씩 모든 군집들이 하나의 군집이 될 때 까지

: 대략적인 그룹(k)의 개수 파악

: cultree(계층 결과, k=군집수) 함수 이용하여 모델의 적정한 cut를 알아낼 수 있음.



~~~R
## 계층적 군집화 예제

library(ggplot2)
data(diamonds)
head(diamonds)
str(diamonds)
 # 10개의 변수 / data.frame / obs 

t <- sample(1:nrow(diamonds),1000) 
t #index가 나옴

test <- diamonds[t,]
dim(test) # 차원수 / (1000,10)라고 예상할 수 있어야 함

mydia <- test[c("price","carat","depth","table")]
 # subset이나 creatdatapatision을 이용해도 된다 

result <- hclust(dist(mydia),method="ave")
 # 줄여서 만든 것, 원리만 이해하도록 1000개만 뽑은 것
 # hclust를 이용하여 
 # 4차원에서 거리 값 구하여 
 # 군집의 대표값 (2개 중에 누구를 선택할 것인가): ave가 average 대푯값을 평균으로 사용하겠다.
 # hclust를 할 때 원본이 아니라 dist 거리 값 , matrix 값을 주어야 한다.

plot(result, hang=-1)
~~~





























참조

https://ratsgo.github.io/machine%20learning/2017/04/16/clustering/

https://mylifemystudy.tistory.com/63

https://leedakyeong.tistory.com/

https://astralworld58.tistory.com/58