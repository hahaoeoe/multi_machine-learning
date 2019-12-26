# 인공신경망(Artifical nerual networks; ANN)



~~~ R
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



## 선생님이 주신 인공신경망 예제

prob <- read.csv("problem.csv", header=T, stringsAsFactors = F)
head(prob)

for(i in 1:30){
  prob[i] <- prob[i] *(1/5)
}

head(prob)

normalize <- function(x){
  return((x-min(x)) / diff(range(x)))
}

sigmoid <- function(x){
  return(1/(1 + exp(-x)))
}


prob$accident2 <- with(prob, ifelse(accident =="suicide" | accident == "violence", 1,0))

head(prob)

library(nnet)
prob <- prob[-31]
m1 <- nnet(accident2~.,data=prob, size =10)
summary(m1)
r1 <- predict(m1,prob)
head(r1)

cbind(prob$accident2, r1 >0.5)
sum(as.numeric(r1>0.5) != prob$accident2)

 # 같은 방법 다른 패키지
install.packages("neuralnet")
library(neuralnet)

xnam <- paste0("ans", 1:30)
fmla <- as.formula(paste("accident2 ~", paste(xnam, collapse="+")))
m2 <- neuralnet(fmla, data = prob, hidden = 10)
plot(m2)

~~~





