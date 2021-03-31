# 추천 알고리즘 구현
 - 파이썬을 활용한 추천알고리즘 구현 연습
 - [MovieLens](https://grouplens.org/datasets/movielens/) 데이터셋 활용


<br />
<br />

### #1. 무비렌즈(MovieLens) 데이터를 통한 간단한 평점 데이터 탐색
 - 각 데이터프레임의 기초통계량 분석
 - 데이터프레임의 'groupby' method 활용하여 분류
 - 데이터프레임의 'sort_values' method 활용하여 정렬
 - 히스토그램을 활용하여 특정 영화의 평점분포 확인
___


### #2. 간단한 추천시스템 구현해보기
 - 총 4가지의 방법을 사용하여 평점 예측
 - 방법에 대한 성능평가는 RMSE 값 사용
   + 단순랜덤예측           : 1.92
   + 영화평균 평점기반 예측 : 1.03
   + 사용자평균 평점기반 예측 : 0.94
   + 장르별 평점기반 예측 : 1.06
 - 사용자 평균 기반으로 한 예측모형이 가장 RMSE값이 낮게 나타났다.
 - 즉, 사용자를 중심으로 모델링을 해야 성능이 향상 됨을 간단하게나마 확인할 수 있었다.
   
___

### #3. TF-IDF를 이용한 추천알고리즘
  - 컨텐츠기반 추천시스템
    + 정보를 찾는 과정와 과거 정보를 활용하여 유저의 성향캐치
    + Feature Extraction, Feature간 유사성 파악
    + 컨텐츠분석 -> 유저프로필 파악 -> 유사아이템 선택 -> 추천리스트 생성
  - TF-IDF
    + 각 단어에 가중치를 부여하여 Keyword Extraction 등에 활용
    + TF : 단어 w가 문서 d에 등장한 빈도 수
    + DF : 단어 W가 등장한 문서 d의 수
  - 컨텐츠 유사도는 cosine similarity 사용
  - 성능평가 방법 : RMSE
    + RMSE 값 : 1.18
  - 결과
    + 성능이 눈에 띄게 좋아지지 않음
    + 어떤 Feature를 사용하느냐가 핵심인 것 같다.
  - Self FEEDBACK
    + List comprehension 공부를 더 해야 될 것 같다... list comprehension 내 이중 for 문 구문도 연습해야겠다.
    + 데이터를 원하는 방식대로 가공하는 연습이 필요한 것 같다.
___

### #4. 이웃기반 협업필터링
  - 아이템 기반 협업필터링
  - 유저 기반 협업필터링
  - sparse matrix를 만들어 기준이 되는 아이템을 만든다.
  - cosine similarity 구함
  - 결과
    + 아이템 기반 : 0.81
    + 유저 기반   : 1.69
  - Self FEEDBACK
    + loc, apply, unstack 용법 등에 대해 다시 한번 확인해볼 필요가 있다.
 ___

### #5. 모델기반_협업필터링 및 Matrix_Factorization
  - 특이값 분해(SVD)를 활용한 Latent factor 활용
    + 이 때 hyperparameter : K
  - matrix_factorization library 활용
  - 결과
    + 아이템 기반 : 0.82
    + 유저 기반   : 0.85
  - Self FEEDBACK
    + np.linalg.svd 사용법을 익히자
 ___

### #6. 모델기반 협업필터링 및 협업필터링 성능 비교 분석
  - SGD 구현 및 optimizer 알고리즘 구현
  - 결과
    + __movie lens 데이터는 *아이템 기반으로 모델링*을 하는 것이 다른 모델보다 더 우세한 결과가 도출되는 것으로 보인다.__
  - Self FEEDBACK
    + 각 방법이 확실하다 라는 정답은 없다
    + 여러 모델들을 구현하고 여러번의 시도를 해서 최적의 모델을 찾는 방향으로 모델링을 해야겠다.
