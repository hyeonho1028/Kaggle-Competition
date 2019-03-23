# Kaggle Competition

#### My kaggle
1. 아이디어
	1. 정리하기
	2. 구현하기
	3. 유명한 아이디어 구현하기(아이디어의 이유와 구현하기)

2. 탐색적 데이터 분석 전략
	1. 나만의 EDA 해보기
	2. high vote kernels 탐색 후 이해
	3. 가설과 가정을 세우고 증명하기

3. 피쳐 엔지니어링 전략
	1. 나만의 피쳐 엔지니어링 해보기
	2. high vote kernels 탐색 후 이해
	3. 무한대, 무한정으로 진행해보기
	4. point
        1) 문제유형을 정확하게 파악한 후 피쳐 엔지니어링을 진행하여야 한다.
        2) image classification : scaling, shifting, rotations(CNN)
        3) sound classifications : fourier, mfcc, specgrams, scaling
        4) text classification : tf-idf, svd, stemming, spell checking, stop words' removal, x-grams
        5) time series : lags, weighted averaging, exponential smoothing
        6) categorical : target enc, freq, one-hot, ordinal, label encoding
        7) numerical : scaling, binning, derivatives, outlier removals, dimensionality reduction
        8) interactions : multiplications, divisions, group-by features
        9) recommenders : features on transactional history, item popularity, frequency of purchase
        10) data cleaning and preparation
        11) handle missing value
        12) generate new feature(other problems require different feature engineering)
        13) can be automated(Discover pattern)

4. 모델링 전략
	1. 나만의 모델링 해보기
	2. high vote kernels 탐색 후 이해
	3. hyper parameter 는 마지막에
	4. point
        1) the type of problem defines the feature engineering
        2) image classification : CNNs (Resnet, VGG, densenet)
        3) sound classifications : CNNs(CRNN), LSTM
        4) text classification : GBMs, Linear, DL, Naive bayes, KNNs, LibFM, LIBFFM
        5) time series : Autoregressive models, ARIMA, linear, GBMs, DL, LSTMs
        6) categorical features : GBMs, Linear models, DL, LibFM, libFFm
        7) numerical features : GBMs, Linear models, DL, SVMs
        8) interactions : GBMs, Linear models, DL
        9) reommenders : CF, DL, LibFM, LIBFFM, GBMs
	5. 모델과 데이터에 대한 이해를 한 뒤에 사용하는 것이 가장 중요 포인트라고 생각함. 또한 항상 옳은 것만은 없으므로 비판적인 사고도 필요하다는 생각을 한다.

5. 앙상블 전략
	1. 캐글에서는 주로 stacking(blending) 기법을 사용한다.
	2. 단순 평균에서 멀티레이어 스태킹 등 다양한 방법으로 결합한다.

6. 협업
	1. team merge
		1) 1회 정도 merge team 해서 시행해 보았으나, 역할 분담에 어려움을 느꼈으며, 리더가 있어야지 원활할 것이라는 생각이 든다. 

7. tip
	1. Discussion을 생활화하여 글 작성 및 올라오는 글들을 읽어보자.
	2. 유명 커널의 댓글을 보는 생활화를 하자
	3. 캐글을 커뮤니티 하듯이 항상 습관적으로 접속하고 확인하고 생각하자
	4. 나만의 커널을 만들고, 궁금한 부분은 디스커션에 정리해서 질문해보자!
	5. 활발한 커뮤니티 사용을 해보자!


## My kaggle Competition

### [1. Google Analytics Customer Revenue Prediction](https://www.kaggle.com/c/ga-customer-revenue-prediction)

### 기간
2 months

### Description
The 80/20 rule has proven true for many businesses–only a small percentage of customers produce most of the revenue. As such, marketing teams are challenged to make appropriate investments in promotional strategies. 
RStudio, the developer of free and open tools for R and enterprise-ready products for teams to scale and share work, has partnered with Google Cloud and Kaggle to demonstrate the business impact that thorough data analysis can have. 
In this competition, you’re challenged to analyze a Google Merchandise Store (also known as GStore, where Google swag is sold) customer dataset to predict revenue per customer. Hopefully, the outcome will be more actionable operational changes and a better use of marketing budgets for those companies who choose to use data analysis on top of GA data.

### [My Kernel](https://github.com/hyeonho1028/Kaggle_Competition/tree/master/Google%20Analytics%20Customer%20Revenue%20Prediction)

### 최종결과
1. submit count : 
2. 등수 : /4111



### [2.Quora Insincere Questions Classification](https://www.kaggle.com/c/quora-insincere-questions-classification)

### 기간
3 months

### Description
An existential problem for any major website today is how to handle toxic and divisive content. Quora wants to tackle this problem head-on to keep their platform a place where users can feel safe sharing their knowledge with the world.
Quora is a platform that empowers people to learn from each other. On Quora, people can ask questions and connect with others who contribute unique insights and quality answers. A key challenge is to weed out insincere questions -- those founded upon false premises, or that intend to make a statement rather than look for helpful answers.
In this competition, Kagglers will develop models that identify and flag insincere questions. To date, Quora has employed both machine learning and manual review to address this problem. With your help, they can develop more scalable methods to detect toxic and misleading content.
Here's your chance to combat online trolls at scale. Help Quora uphold their policy of “Be Nice, Be Respectful” and continue to be a place for sharing and growing the world’s knowledge.

### Important Note
Be aware that this is being run as a Kernels Only Competition, requiring that all submissions be made via a Kernel output. Please read the Kernels FAQ and the data page very carefully to fully understand how this is designed.

### 최종결과
1. submit count : 
2. 등수 : /4111

### [3.미정]()

