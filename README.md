# GaOn_chart_Forecasting

## 1. 프로젝트 배경
음악차트의 어떤 장르를 사람들이 많이 듣고 그 월 별 추세가 어떤 지 파악하고 자 진행하게 됨.
## 2. 데이터 수집
circle 차트의 Digital Chart 부분에서 월 별로 Rank, Rank 변화, Title, Artist, Score과 Play 버튼을 마우스 오버하면   
벅스 사이트에서 장르와 발매일을 Selenium 을 이용하여 2018년 1월 부터 2023년 6월까지 크롤링  
(Score 는 스트리밍, 다운로드, BGM, V컬러링 판매량에 가중치를 부여하여 집계한 값이다)  
## 3. 데이터 전처리
장르가 여러개인 경우 처음 소개되는 장르를 선택했고,    
각 월별 장르별 Score 값을 합산하여 나타냄    
랩, 인디, 발라드, 댄스, 팝 5가지를 사용.  
## 4. EDA 및 모델링
![image](https://github.com/lkj626/GaOn_chart_Forecast/assets/23254702/5a3aaacd-0ae3-4b7f-b72f-a7722f4998a4)  
![image](https://github.com/lkj626/GaOn_chart_Forecast/assets/23254702/3891282a-1679-4c19-bb8b-4dfaaa16cf01)

데이터 시각화와 ADF 검정을 통해서 각각의 5가지 장르의 Stationary 를 확인함.  

랩, 발라드, 팝의 p-value 값을 판정했을 때 Non Stationary 해서 differencing 진행  

train 데이터를 첫날 대비 변화량으로 정규화를 진행  

VAR Order 를 AIC 기준으로 선택후 예측

## 5. 결과
![image](https://github.com/lkj626/GaOn_chart_Forecast/assets/23254702/3ed972f4-87b0-4974-bd67-baef8ca1dbae)

VAR 추정할 계수가 많아지면, 예측에 들어오는 추정 오차가 커져서 예측 오차가 컸다  
어느정도 증감 추세가 일치하는 부분도 있었지만, 크게 벗어난 경우도 있었음.  
