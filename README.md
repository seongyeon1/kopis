# KOPIS 문화공연데이터 분석
## 문화향유인원 증가를 위한 공연장 최적화 방안 모색

# 개요
## 1) 분석 목적
- 재작년부터 시작된 코로나19의 유행으로 인해 문화소비, 특히 공연관람과 관련한 소비가 미진하다. 백신 접종율의 증가로 각종 규제가 풀려가고 있는 이 시점, 침체된 공연계를 부흥시키고 공연의 소비를 늘리기 위한 방안을 마련하여야 한다.
- 이를 위해 관객 예매정보를 중점적으로 어떤 관객이 공연을 많이 보러 오는지 파악하고, 관객정보 외 공연 예매량에 영향을 미칠수있는 요인을 파악해서 공연장을 최적화하는 방안을 모색한다.
- 이를테면, 필자를 포함한 20대의 경우 대학생 또는 사회초년생으로, 비교적 가격이 저렴하거나 할인율이 높은 공연을 선호할 것이라는 추론이 가능하다. 공연 관람을 위해 먼 거리를 이동해 오거나 큰 지출을 불사하는 관객들의 경우, 해당 장르의 열렬한 팬이거나 부동의 소비자층일 가능성이 높다는 추론 역시 가능하다. 이러한 추론을 바탕으로 관객유형에 맞는 공연을 추천하는 시스템을 구현하고자 한다, 

## 2) 배경 및 필요성
### 1. 배경
- 현재는 데이터가 많이 부족하나, 공공데이터포털의 ‘적절하다고 생각하는 한달 여가 비용’ 이라는 데이터에서 성별, 연령별, 지역별 항목을 추출하여 비교해 현황을 분석해 보았다.
- 실제 예매 자료도 함께 파악해보고자 하였으나 자료가 부족하여 인터파크의 예매 통계분석 자료를 참고하였다.
 
#### 성별/연령별 분석

![image](https://user-images.githubusercontent.com/83098550/143206719-08dcc02b-5eaa-45e5-aaac-0a9d31cc9ba1.png)
![image](https://user-images.githubusercontent.com/83098550/143206922-13037e65-167f-4015-bb91-e704b2f1cd1f.png)

15-`19세, 70대 이상의 연령층에서는 여가 비용을 15만원 이상 지불할 의향이 타 연령층과 비교했을 때 현저히 떨어짐을 확인할 수 있었으며, 30대, 50대, 20대와 40대 순으로 여가에 높은 비용을 기꺼이 지불할 용의가 있다고 답했다. 이들은 곧 20대~50대, 특히 30대와 50대가 공연 매출의 상당부분을 차지하고 있는 주 고객층이라는 잠재적 결론으로 이어질 수 있었다. 

또한, 2020년 인터파크에서 판매한 공연 티켓을 구매한 예매자 전체를 대상으로 성별 연령별 분포를 살펴본 자료에 따르면, 여성이 77%, 남성이 23%의 비중으로 2019년에 비해 여성 관객 비중이 5% p 증가했으며, 여성 예매자는 2016년 69%, 2017년 71%, 2018년 72%, 2019년 72%로 해마다 조금씩 증가하는 추세를 보이고 있다.

여성들 중에서는20대(28%), 30대(24%), 40대(13%) 순으로 높은 예매자 비중을 보였는데 특히20대 여성에서 전년 대비3% p, 50대 여성 관객이2% p 증가한 것으로 나타났다. 남성은 30대(8%), 20대(7%), 40대(5%)의 순으로 높은 예매자 비중을 보이고 있다. 전체 예매자 중에서는 20대 여성과 30대 여성이 52%로 공연 시장의 주축을 이루는 핵심 고객층임을 알 수 있다.
 

#### 지역별 분석

![image](https://user-images.githubusercontent.com/83098550/143206961-39fce126-ac3a-47ae-97ea-7cb6a57bc9d5.png)

먼저 2019년과 2020년의 공연건수를 비교했을 때, 전 지역에서의 공연건수는 감소하였다는 것을 확인할 수 있다.

![image](https://user-images.githubusercontent.com/83098550/143206987-1f20ff5d-2b44-4198-a19c-1adc14070f7e.png)

다음으로 파이차트로 지역 비중을 파악해 보았다. 2020년 공연건수는 서울이 55.89%로 과반수를 차지하였으며 서울과 경기를 합치면 전국 공연 수의 약 63%로 코로나19 영향으로 지역 문화 행사가 더욱 움츠러들면서 2019년 57.8% 대비 서울 경기권의 쏠림이 더 심화되었다.
 
또한, 2020년 인터파크에서 판매된 전체 공연 총 4,310편을 전국 광역 시도별로 분류해 본 자료에서도 마찬가지로, 서울에서 올려진 공연이 2,690편으로 전체의 62.4%를 차지했고 뒤를 이어 경기도가 359편으로 8.3%를 차지하였다 서울과 경기를 합치면 전국 공연 수의 70.7%로 2019년 63.1%와 비교했을 때 서울 경기권의 쏠림현상이 더 심화되었음을 보여주었다.

![image](https://user-images.githubusercontent.com/83098550/143207008-4c2add34-9139-4047-940f-a96e4248b486.png)

다음으로 매출액 비중을 파악해 보기위해 파이차트로 나타내 보았다. 매출액은 서울에서만 전체의 88.64%를 차지했다. 경기 지역도 5.08%에서 1.53%로 매출이 2019년 75.89% 대비 서울의 쏠림현상이 더 심화되었음을 보여주었다. 이는 유료공연의 비중이 서울에서 특히나 더욱 집중되어 있음을 예측할 수 있다. 

### 2. 필요성
![image](https://user-images.githubusercontent.com/83098550/143207034-5e80b02d-2193-434c-9aa2-738b3abd4843.png)
지역별로 공연비용에 대해 비용을 지불할 용이가 있는 금액을 파악해 보고 싶었으나 자료가 없어 통계청에서의 ‘적절하다고 생각하는 여가비용 한 달 평균’ 데이터를 통해 유사하게 나마 파악해보았다. 여가에는 다양한 요소들이 있고, 매출액에서도 타지역의 사람들이 방문해서 공연을 본 비중도 있을 것이기에 오류가 있겠지만, 타지역에서도 여가, 즉 공연에 대한 수요가 서울 못지 않음을 유추할 수 있다.
‘문화적 권리’라는 말이 있는 만큼 문화는 누구나 쉽게 접근할 수 있고 향유할 수 있어야 한다. 지역별 문화 향유의 격차를 줄이고 향유인원을 늘리기 위한 방안의 필요성이 요구되는 시점이다.

## 3) 차별성 및 독창성
앞서 파악해본 현황과 필요성을 바탕으로 제기된 문화향유 격차의 문제를 해결하고, 코로나 시대의 문화향유 인원을 늘리기 위한 방안으로 공연장 자체를 최적화하는 방안을 생각하였다. 즉, 관객의 수요를 예측하여 관객이 좋아할만한 공연으로 구성된 이상적인 공연장은 무엇인지 파악해 볼 것이다.
 이번 분석은 문화 향유의 지역격차를 줄이기 위해 공연장 혹은 공연을 늘렸을 때 실질적인 효과성이 있는지 검증해 나가는 과정까지 나아갈 것이며 어떤 공연으로 구성해야 매출과 예매가 늘어날 수 있는지 예측해볼 것이다. 
 
## 4) 주요 내용
각각의 공연장의 위치에 따라 어떤 공연을 상영하는 것이 인기 있을지 추천해주고 나아가 지역별 인구수로 공연장이 가장 부족한 곳을 찾아 공연장이 지어진다면, 어디에 짓는 것이 가장 시급하고 관객 유치에 효과가 좋을지 찾아 볼 것이다.

# 세부 내용
## 1) 분석 방법
- 먼저, 공연장과 공연, 유동인구수, 유동인구 비중, 매출 등의 상관관계를 파악해 볼 것이고, 유의미한 상관관계가 있는 요인들을 바탕으로 공연의 매출, 예매수를 늘릴 방안을 파악하기 위해 분석을 해볼 계획이다. 공연 관계자의 입장에서는 매출을 늘리고, 관객의 입장에서는 접근성을 늘리기 위해서는 먼저, 관객의 유형을 파악해 보는 것이 우선이다.
   -> 이를 위해서 각각의 공연 코드, 장르, 예매자료를 활용하여 공연 코드, 장르 별로 어떤 소비자들에게 인기가 있는지 분석하고, 공연 코드과 장르에 따른 관객을 학습한다. 
   -> 공연에 대한 자료들은 필요하다면 크롤링을 해서 자세하게 선호하는 유형을 학습할 계획이다.
- 다음으로 기존 공연장에 대한 자료가 필요하다. 공연장 주변 유동인구를 바탕으로 관객의 인구 유형을 유추해볼 계획이다.
   -> 공연장 근처 유동인구 유형자료를 바탕으로 공연장의 관객유형을 파악해 어떤 관객들이 많이 공연을 보러오는지 파악할 수 있다. 
   -> 예를 들어서 공연장 근처 유동인구 자료로 데이트 코스로 커플이 많이 오는 곳인지, 가족들이 많이 방문하는지 등의 인구유형을 유추해 본다. 
      공연장이 주로 데이트 코스로 오는지, 가족 나들이 장소로 자주 오는 곳인지에 따라서 공연의 유형도 달라질 것이라 예상되기 때문이다. 
   -> 이 자료들을 바탕으로 유동인구 유형에 맞는 공연을 추천해 어떤 공연을 상영할지 추천까지 해 줄 수 있을 것이다.
- 또한, 각 공연장별 장르 비중을 분석해서 현재의 상영하고 있는 공연이 주변 유동인구, 관객의 유형과 유사한지 파악을 해서 어떤 장르를 늘리면 더 좋을지 제안을 해주는 것으로도 활용하여 현재 공연장의 공연 상영의 의사결정에도 도움을 줄 수 있다.
- 사업자의 입장에서 할인여부를 결정할 때, 지역별, 성별, 연령별 가격 민감도를 분석해 보고 어느 정도의 할인을 했을 때 예매율과 매출이 가장 높을지 예측해본다.
 
- 공연예술통합전산망 보유 데이터를 분류해보면, 공연장에 관한 주요 데이터로는 주소, 장애시설, 편의시설, 주차시설, 부대시설 등이 있으며, 공연에 관한 주요 데이터로는 공연일시, 출연진, 할인금액, 관객에 관한 주요 데이터로는 예매일시, 예매연령, 성별 등이 있다.
- 위 요인들 간의 상관관계를 분석하고, 이를 바탕으로 머신러닝 알고리즘을 활용하여 각 공연의 공연장에 따른 예매율을 예측하고, 추천 시스템 알고리즘을 활용하여, 해당 공연장에서 어떤 공연을 상영할지 추천해준다.

## 2) 분석 가능성
- KOPIS에서 풍부한 데이터를 제공받을 수 있다. 공연예술통합전산망 보유 데이터 안에 성별과 연령 자료가 포함되어 있다. 이를 바탕으로 공연코드, 공연장 코드 별로 성별과 연령의 유의미한 차이가 있는지 분석해 보고, 공연장의 주소를 바탕으로 지역을 나눠서 분류를 진행해 볼 예정이다. 
- 공연 수요 예측을 위해서 sklearn에서 앙상블 모델를 이용할 것이다. dacon 식수예측과 kaggle에서 bike sharing 수요 조사 예측을 해본 경험이 있는데 이를 해본 경험을 바탕으로 공연 수요 예측도 가능할 것이라 생각한다.
- 어떤 소비자층이 가격이나 할인여부에 민감하게 반응하는지를 설명하는 가격 탄력성을 구하기 위해서는 선형 회귀 기법을 사용할 수 있을 것이다. 추천 시스템은 협업 필터링을 사용할 것이며 모든 분석과정은 파이썬을 이용하여 구현할 계획이다. 

## 3) 적용 방향
- 공연지역/공연일시/좌석수/판매기간 등은 사실 판매량이나 매출에 영향을 미치는지 증명되지 않았는데, 이번 분석을 통해 이 중, 또는 이 외에도 어떤 요인이 공연매출에 크고 작은 영향을 미치는지 파악할 수 있고 앞으로 공연주체자의 입장에서 의사결정을 내리는데 도움을 줄 수 있다.
- 장르별 ‘타깃층 설정’에 도움을 줄 수 있다. 어떤 장르의 공연이 어떤 소비자에게 인기가 있는지 알아보고 이를 바탕으로 공연업계 측에서는 해당 소비자에 대한 공연 접근성을 강화한다거나, 중점적으로 마케팅을 진행하는 등의 노력을 취할 수 있다.
- 가격이나 할인율은 공연 뿐 아니라 다른 재화나 서비스를 구매하는데 있어서도 큰 영향을 끼치는 주요요인이다. 가격이 아무리 높아도, 할인을 하지 않더라도 티켓 구매가 조기 마감되는 공연이 있는 반면 가격 책정이 티켓판매량에 큰 영향을 끼치는 공연도 있다. 또한 가격에 민감하게 반응하는 소비자가 누구인지 역시 파악할 수 있어 공연의 가격책정에 있어서도 활용이 가능할 것이다.

- kopis에서는 ‘공연통계’라는 카테고리에서 기간별, 지역별, 장르별 등으로 나누어 ‘공연’에 대한 정보를 제공하고 있다. 종사자 수, 공연팀당 연간 평균 공연 횟수 등까지 나와 있을 정도로 공연 자체에 대한 정보는 비교적 자세한 편이나 소비자에 대한 정보는 찾아보기 힘들다. 소비자에 대한 통계 역시 kopis에서 제공할 수 있게 될 것이다.

## 4) 기대효과
- 앞서 확인했듯이 문화 향유에 대한 욕구는 지역과 상관없이 나타나지만 공연 횟수나 매출액은 수도권이 전체 공연의 과반수 이상을 차지하였다. 이번 분석을 통해 소비자 유형별 선호하는 공연이 무엇인지 알아보고, 더 나아가 이를 활용하여 어느 지역에 공연장을 신설하거나 공연을 늘릴 필요가 있는지 확인할 수 있을 것이다. 이를 통해 문화 향유의 지역격차를 줄이고 궁극적으로는 문화산업의 향유계층을 늘릴 수 있을 것이라 기대한다. 또 가격적인 측면에 있어서 소비를 확대하기 위해서 공연업계는 어떤 방향으로 나아가야 할 지에 대한 나침반 역할을 할 수 있을 것이라 기대한다. 
- 이번 분석은 현재 공연장의 장르 비중이나 예매율을 분석한 자료를 바탕으로 현재 공연장이 최적화된 상태로 잘 운영되고 있는지 파악하는 데에도 도움을 줄 수 있을 것으로 기대되고 나아가 앞으로 공연장 입지 선정을 하는 과정까지도 도움을 줄 수 있을 것으로 기대된다.

#### 활용자료
적절하다고 생각하는 여가비용(한 달 평균), KOPIS, 2019
지역별 통계현황, KOSIS, 2019
지역별 통계현황, KOPIS, 2020
2020 인터파크 공연 결산1 - 판매 금액, 예매자 분석, 인터파크, 2020
