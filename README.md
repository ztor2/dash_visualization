# Interactive Visualization with Dash, Plotly and Cytoscape<br>
<br> Dash, Plotly와 Cytoscape를 이용한 반응형 시각화 구현.

<br>

### 연구 배경 및 목적
- 이 저장소의 코드는 중소기업기술정보진흥원 주관의 '2020 기술혁신개발사업'에서 ㈜아이패밀리에스씨 R&D Center와 서울과학기술대학교가 협력 수행 중인 '**화장품 소비자 분석 시스템 프로젝트**'에서 데이터 시각화 파트 수행을 위해 작성되었다.
- Plotly는 d3.js, stack.gl 기반의 high-level 그래프 라이브러리이며, Dash는 Plotly.js와 React.js를 기반으로, 파이썬(Python), R, 줄리아(Julia), F# 언어에 최적화된 데이터 앱 구축 라이브러리이다.
- Dash와 Plotly를 이용해, 데이터 분석 언어로 널리 쓰이는 Python으로 다양한 기능을 제공하는 interactive 시각화가 가능하며 대시보드(dashboard) 형태의 시각화도 구현해볼 수 있다.
- Cytoscape.js는 네트워크 시각화 라이브러리며, Plotly와 같이 Dash에서 파이썬 언어로 사용할 수 있도록 구현되어 있다.
- 이 저장소는 화장품 정보 샘플 데이터를 이용해 Dash, Plotly, Cytoscape로 반응형 시각화를 구현하는 코드를 포함한다.

<br>

### 코드 파일 설명

- **lipgloss_category_analysis.ipynb:** Dash와 Plotly를 이용해 제품별 리뷰 수, 브랜드 분포, 브랜드별 평균 가격 그래프를 시각화하고 이를 대시보드화 하는 코드 파일.
- **dash_network.ipynb:** Dash와 Cytoscape를 이용해 제품 리뷰 키워드 네트워크를 시각화하는 코드 파일.
- **lipgloss_category.json:** lipgloss_category_analysis.ipynb 파일의 시각화에 필요한 샘플 데이터 파일.
- **product_6015_elist.json:** dash_network.ipynb 파일의 시각화에 필요한 샘플 데이터 파일.

<br>

### Dash, Plotly와 Cytoscape 시각화 프로세스

<br>

<p align="center"> <img src="https://i.esdrop.com/d/fha5flk1blzo/5fOAsZGULn.PNG" width="80%" align="center"> </p>
<p align="center">  <b> 그림 1. </b> Dash, Plotly와 Cytoscape의 기본적인 시각화 프로세스. </p>

<br>

### 데이터셋

<br>

<p align="center"> <img src="https://i.esdrop.com/d/fha5flk1blzo/rXY5GFUMd5.png" width="60%" align="center"> </p>
<p align="center">  <b> 그림 2. </b> 시각화에 사용할 화장품 정보 데이터셋. </p>

<br>

### 연구방법 및 결과

<br>

#### 제품별 리뷰 수 Top N

1. 리뷰 수(review_count)를 제품명(product_name)과 함께 내림차순으로 정렬 후, 인덱스를 재정렬한다. 
2. plotly.express의 bar 그래프 함수를 이용해 막대 그래프를 그린다.
3. 특정 제품의 리뷰 수가 지나치게 많은 경우가 있으므로, y축에 log 스케일을 적용하는 것이 좋다.
4. 그래프 선언 후, update 기능을 이용해 그래프 세부사항을 업데이트해준다.
5. 그래프를 app.layout에 dcc.Graph 변수로 할당 후 결과를 확인한다.

<p align="center"> <img src="https://i.esdrop.com/d/fha5flk1blzo/dUFkND35fI.gif" width="60%" align="center"> </p>
<p align="center">  <b> 그림 3. </b> Dash와 Plotly를 이용한 제품별 리뷰 수 Top 30 막대 그래프. </p>

<br>

#### 브랜드 분포

1. 브랜드명(brand_name)과 제품 가격(product_price) 정보를 추출한 후, 인덱스를 재정렬한다.
2. pandas의 value_counts 기능을 이용해 브랜드 출현 빈도를 계산 후, 빈도의 내림차순으로 정렬한다.
3. 정렬 후 상위 20개 브랜드를 추출해 시각화한다.
4. plotly.express의 pie 그래프 함수를 이용해 파이 그래프 개체를 만든다.
5. 그래프 선언 후, update 기능을 이용해 그래프 세부사항을 업데이트해준다.
6. 그래프를 app.layout에 dcc.Graph 변수로 할당 후 결과를 확인한다.

<p align="center"> <img src="https://i.esdrop.com/d/fha5flk1blzo/ZKSS5xtDSd.gif" width="50%" align="center"> </p>
<p align="center">  <b> 그림 4. </b> Dash와 Plotly를 이용한 브랜드 분포 파이 그래프. </p>

<br>

### 브랜드별 평균 가격

1. 브랜드 분포 시각화에서 선택된 20개 브랜드에 대한 가격(product_price)을 추출한 후, pandas의 groupby-mean 기능을 이용해 각 브랜드의 평균 가격을 계산한다.
2. 가시성을 높이기 위해 가격을 내림차순으로 정렬한다.
3. plotly.graph_objects의 scatter plot 그래프 함수를 이용해 그래프를 구성한다.
4. 그래프 선언 후, update 기능을 이용해 그래프 세부사항을 업데이트해준다.
5. 그래프를 app.layout에 dcc.Graph 변수로 할당 후 결과를 확인한다.

<p align="center"> <img src="https://i.esdrop.com/d/fha5flk1blzo/KREp79ds30.gif" width="50%" align="center"> </p>
<p align="center">  <b> 그림 5. </b> Dash와 Plotly를 이용한 브랜드 평균 가격 산포도 그래프. </p>

<br>

### 리뷰 키워드 네트워크 그래프

- 리뷰 데이터로 구축한 키워드의 관계 데이터로 네트워크를 구축해본다.
1. Edgelist 형식으로 데이터를 구축하며, weight는 PMI(pointwise 2. mutual information)을 계산한 후 정규화하여 사용한다.
3. 데이터의 노드, 링크들을 elements에 할당할 수 있도록 데이터 형식을 맞추어 변수에 저장한다.
4. Cytoscape 개체의 elements에 노드와 링크를 추가해 네트워크를 구축한다.
5. stylesheet 변수에 네트워크의 각종 옵션을 설정한다.
6. Callback 기능을 이용해 interactive 기능을 추가한다.
7. 네트워크를 확인하고, 네트워크의 특징에 따라 노드의 크기, 데이터 수, 레이아웃 등을 조정한다.

<p align="center"> <img src="https://i.esdrop.com/d/fha5flk1blzo/QHhDEQDGqU.gif" width="50%" align="center"> </p>
<p align="center">  <b> 그림 6. </b> Dash와 Cytoscape를 이용한 화장품 리뷰 키워드 네트워크 그래프. </p>

<br>
