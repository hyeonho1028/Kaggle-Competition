## Join competition
### [1. Google Analytics Customer Revenue Prediction](https://www.kaggle.com/c/ga-customer-revenue-prediction)

### Date
2 months

### Description
The 80/20 rule has proven true for many businesses–only a small percentage of customers produce most of the revenue. As such, marketing teams are challenged to make appropriate investments in promotional strategies. 
RStudio, the developer of free and open tools for R and enterprise-ready products for teams to scale and share work, has partnered with Google Cloud and Kaggle to demonstrate the business impact that thorough data analysis can have. 
In this competition, you’re challenged to analyze a Google Merchandise Store (also known as GStore, where Google swag is sold) customer dataset to predict revenue per customer. Hopefully, the outcome will be more actionable operational changes and a better use of marketing budgets for those companies who choose to use data analysis on top of GA data.

### [My Kernel](https://github.com/hyeonho1028/Kaggle_Competition/tree/master/Google%20Analytics%20Customer%20Revenue%20Prediction)

### Result
1. submit count : 
2. 등수 : /4111

---
#### Season-1
##### Data Load
1. fread 혹은 read.csv만 사용하다가 read_csv를 처음 사용해 봤는데, 좋은 느낌이 들었다. fread보다 빠른지는 확인을 안해봐서 확실하지는 않지만, 대용량 csv를 불러올 때, 괜찮다는 느낌을 받았다.
2. str로 데이터의 structure를 확인하였느나, glimpse를 사용했는데 더 좋았다.(정렬되어 나오는 부분)
3. JSON파일형식을 처음으로 다루어 봤는데, json파일을 다루는 방법과, parsing, flatten 등의 방법을 익혔다.

##### Explortary Data Analysis
###### 1 unique row
1. 중복 된 행들을 확인하는 작업을 했다. 중복 된 행들은 잘못된 데이터라고 판단을 하였고(매출에 관한 데이터가 동시에 2번 이루어지는 것은 전산 오류이거나, 잘못 수집된 데이터라고 판단하였다.) 제거하였다.
###### 2 train set과 test set column의 차이
1. train set에는 있지만, test set에는 없는 컬럼이 있었다. 그 이유를 정확하게 알 수는 없지만, test set에서 만들 수 없는 컬럼이라고 판단을 하였고, train set의 column을 제거하였다.
###### 3 missing value
1.. missing value에 대한 이슈가 굉장히 흥미로웠다. 나는 평소에 missing value를 제거하거나, 어떤 특정값(mean, median, 높은 빈도 값) 등으로 대체 했었는데, 캐글러들은 결측값을 'Not value'라는 값으로 그대로 사용하는 것이 매우 흥미로웠다. 아마 예컨데, 계산상의 편리함, 특정값으로 대체하는 방법과 별로 차이가 없거나 더 높은 성능을 유도할 수 있기 때문이 아닌가 싶다.

2. 베이지안 방법론을 공부하고 있는데, 사후분포를 계산해서 결측값을 채우는 방법이나, MCMC를 이용하는 방법 등 여러가지 방법이 굉장히 많은 듯 하다. 조금 더 공부가 필요하다고 여기고 있다.
3. 또한 여러컬럼이 모두 결측값인 경우도 있었다. 그 컬럼은 제거 하였다.
###### 4 outlier value
1. 이상값의 경우 탐지하기도 어렵고, 주관적인 판단이 내포될 수 밖에 없다고 느꼈다. 나의 생각, 캐글러들의 각각의 생각이 상당부분 다른 부분이 많이 보였다. 나의 경우 scaling을 취해주었고, 너무 심한 outlier에 대해서는 제거 하였다.
###### 5 driven variable and feature engineering
1. 캐글은 이 항목이 가장 중요하다. 모든 모델이 그렇듯 input이 좋아야 output이 좋을 수 밖에 없다고 생각한다. 1~4번의 과정을 실시하며, 데이터에 대한 이해를 완벽하게 하였다면, 이해를 기반으로 어떠한 모델을 사용하는 것이 좋을 지 생각해야 되고, 모델에 적절하게, 파생변수들과 차원을 관리해야 한다.
2. 시계열에 대한 컬럼이 있었기 때문에, (연, 월, 일, 분기 별)로 파생변수를 만들었다.
3. scale이 너무 차이나는 컬럼에 대해서 scaling을 실시한 컬럼을 추가로 넣어주었다. 각 컬럼은 최대한 제거 하지 않고, 모델링 과정에서 정규화하는 형식으로 영향력을 줄이려고 하였다. 과거에는 변수선택에 중요성이 대두되었엇다고 하지만, 최근에는 강력해진 컴퓨팅 파워로 인해 변수선택보다, 정규화하는 방식을 주로 사용한다고 한다.
4. 연속형 변수들의 경우 분포를 잘 살펴본 후, 범주화 한 컬럼을 만들었다. 범주형 변수의 경우 labeling을 하여, numeric하게 바꿔주기도 하였다.(이 작업은 모델에 따라서 다르게 해주었다.)
5. 또한 중요변수들에 대해서, (중요 변수들은 기본 base model에서 파악했었다.) grouping을 해주고, 각 group에 대해 aggregating을 해주는 형식으로 driven column을 만들었다.
###### 6 new method
1. (a <- 1)
2. a <> param %>% sum()
3. a[, c('hi', 'hello' := NULL]
4. submit <- . %>% as_tibble()
5. ggplot 이용하는 능력

##### Modeling
###### 1 glmnet
1. 가장 빠른 연산 속도를 자랑한다.(연산이 간단하다. least square method)
2. Basic model baseline 설정을 편안하게 할 수 있었다.
3. 
###### 2 xgboost
1. CART기반 boosting기법이다. , 또 gradient descent method 을 사용한다.
2. gblinear를 사용했고, nthread는 100~1000개를 사용했다. feature 차원은 가능한 한 많은 개수를 사용하였다.
3. depth는 최대 개수인 8개를 사용하였고, 과적합의 위험이 있기 때문에 lambda과 alpha로 각각 regularization을 걸어주고 과적합을 방지하였다.
4. 반복횟수는 30분 ~ 1시간 이내로 모델이 학습하는 시간을 조절 하였다.
###### 3 keras
1. 딥러닝을 한적 있지만, 실제로 코딩을 짜본적은 처음이다. 막히는 부분마다 캐글러들의 도움을 받아서 완성하였다. 아직 여러가지 의문점들이 많다.
2. hidden node와 hidden layer의 개수를 설정하는 것이 굉장히 어려웠다. 순전히 경험적인 부분으로만 의존하여 설정하는 경향이 있었다.
3. 
4. ensembles을 했을 때 높은 효율을 보여주었다.
###### 4 catboost
1. 굉장히 특이한 형태의 모델이다. 다른 모델의 경우 알고리즘 특성상 데이터를 변환 시켜 주어야 하는 경우가 다반사인데(labeling, encoding 등) catboost의 경우 범주형 데이터에 대한 처리를 따로 해주지 않아도 사용할 수 있다. 속도도 충분히 빠르기 때문에 매우 만족스러웠던 알고리즘이다.
2. xgb나 xgb의 발전된 형태의 lgbm등의 약점을 보완하여 만든, 알고리즘이라고 한다. 그 장점은 잔차 추정의 분산을 최소로 하면서 바이어스를 피하는  다이나믹 부스팅 방법을 제시한다는 설명이 있다.
3. 단일모델로만 비교한다면 RMSE가 가장 낮은 특징이 있다. 그러나 ensembles을 했을 때는 좋은 효과를 보이지 않았다.
4. 

##### Ensembles
###### 1 simple average method
1. 대체적으로 average method가 간단하고, 편리하긴 하나 비약적인 RMSE의 하락은 없다. 그러나, bias-variance tradeoff를 줄여주는 것은 굉장히 효과적이었다.
###### 2 staking method
1. 솔직히 staking의 논리는 직관적으로는 이해가 가지 않는다. 그러나 낮은 RMSE를 만들기에는 굉장히 유용하다고 생각한다. 처음부터 모델별로 staking을 하기 보다는, 적당한 모델들의 baseline을 만들고, staking을 시도하고, parameter조절을 하는 것이 좋다는 느낌을 받았다.

##### Validation And Submit
###### 1 RMSE
1. validation과의 RMSE를 낮췄음에도, test set과의 RMSE가 커지거나, val - RMSE가 높아지지만, test - RMSE는 낮아지는 현상이 존재했다. variance-bias tradeoff를 신경을 써야 한다는 생각이 들었다.
2. 그러나 대체적으로 val-RMSE가 낮으면 test-RMSE도 낮았다.
###### 2 submit function
1. submit function을 만들어서 사용하는 것이 놀라웠다. 나는 chunk형식으로 만들어서 chunk를 실행 시키는 형식으로 했었는데 submit() <- . 이런식으로 함수를 만들어서 사용하는 점이 굉장히 유용하였고, 객체지향적이라는 느낌도 받았고, 함수의 수정 등의 용이한 점이 굉장히 많았다.
2. 또한 이번 competition은 0으로 시작하는 고객번호가 많았는 데, R로 read_csv를 하면 0이 지워지면서 날라오는 현상이 있었다. 그렇기에, left merge를 했을 시 제대로 merge가 이루어 지지 않는 경우가 있었다. 이를 character형식으로 유지하고 merge하면 잘 되므로, 앞으로 그렇게 하면 될 듯 하다.
3. 또한 y값인 revenue가 굉장히 큰 수 였기 때문에 log1p()를 취해서 사용하였는데, 0인 값들은 log scale가 안되므로 log(x+1)이 식으로 하는 점도 굉장히 흥미로 웠다.

###### 데이터 누수가 일어나, Competition의 목적과 주제가 변경되었음
----
#### Season2
##### 변경된 주제는 미래 데이터를 예측하는 시계열 Competition이 되었음