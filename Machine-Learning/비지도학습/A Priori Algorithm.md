#  연관 규칙 (A Priori Algorithm; Association Rule Analysis)



~~~R
## 연관성 규칙 1

install.packages("arules")
install.packages("arulesViz")
library(arules)
library(arulesViz)

data(Groceries)
Groceries
str(Groceries)
inspect(Groceries)
  ## trnascations를 보려면 inspect함수를 이용해야함 
  ## 하나의 거래 정보를 
  ## 하나하나가 trnasaction / 9834 이 하나가 transactions

summary(Groceries)
  ## 9835 row / 169 colunms => 아이템 대신 이름을 쓰면 된다??? 


sort(itemFrequency(Groceries, type ="absolute"), decreasing = T)

itemFrequencyPlot(Groceries,topN=10, type = "absolute")
itemFrequencyPlot(Groceries, topN = 10, type = "relative")
  # 탐색작업

apriori(Groceries)
result_rules <- apriori(Groceries, parameter = list(support=0.005,confidence = 0.5, minlen=2))
result_rules
summary(result_rules)
inspect(result_rules[1:10])


## 연관성 분석2 선생님 예제 파일

 # 데이터 읽기 / 전처리
getwd()
setwd("C:\\rwork\\MLData")
build <- read.csv("building.csv",header = T)
build[is.na(build)] <- 0
build <- build[-1]
build

 # 연관성 분석
library(arules)
  # 연관성 규칙 분석을 위해 transaction 타입으로 전환시켜함
trans <- as.matrix(build, "Transaction")

trans <- as.matrix(build, "Transaction")
rules1 <- apriori(trans, parameter = list(supp = 0.2, conf =0.6, target = "rules"))
rules1

inspect(sort(rules1))

rules2 <- subset(rules1, subset = lhs %pin% '보습학원' & confidence > 0.7)
inspect(sort(rules2))

rules3 <- subset(rules1, subset = rhs %pin% '편의점' & confidence > 0.7)
rules3
inspect(sort(rules3))

 # Visualizaion
b2 <- t(as.matrix(build)) %*% as.matrix(build)

install.packages("sna")
library(sna)
install.packages("rgl")
library(rgl)

b2.w <- b2 - diag(diag(b2)) 

rownames(b2.w)
colnames(b2.w)

gplot(b2.w , displaylabel = T, vertex.cex = sqrt(diag(b2)), vertex.col = "green", 
      edge.col = "blue", boxed.labels = F, arrowgead.cex = .3, 
      label.pos = 3, edhe.lwd = b2.w*2)

  # SNA: 사회연결망
  # 편의점과 

~~~

