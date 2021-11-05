# Interactive Visualization with Dash, Plotly and Cytoscape<br>
<br> Dash, Plotly와 Cytoscape를 이용한 반응형 시각화 구현.

<br>

### 연구 배경 및 목적
- Plotly는 d3.js, stack.gl 기반의 high-level 그래프 라이브러리이며, Dash는 Plotly.js와 React.js를 기반으로, 파이썬(Python), R, 줄리아(Julia), F# 언어에 최적화된 데이터 앱 구축 라이브러리이다.
- Dash와 Plotly를 이용해, 데이터 분석 언어로 널리 쓰이는 Python으로 다양한 기능을 제공하는 interactive 시각화가 가능하며 대시보드(dashboard) 형태의 시각화도 구현해볼 수 있다.
- Cytoscape.js는 네트워크 시각화 라이브러리며, Plotly와 같이 Dash에서 파이썬 언어로 사용할 수 있도록 구현되어 있다.
- 이 저장소는 화장품 정보 샘플 데이터를 이용해 Dash, Plotly, Cytoscape로 반응형 시각화를 구현하는 코드를 포함한다.

<br>

### Dash, Plotly와 Cytoscape 시각화 프로세스

<br>

<p align="center"> <img src="https://i.esdrop.com/d/fha5flk1blzo/5fOAsZGULn.PNG" width="80%" align="center"> </p>
<p align="center">  <b> 그림 1. </b> Dash, Plotly와 Cytoscape의 기본적인 시각화 프로세스. </p>

<br>

### 데이터셋

<br>

<p align="center"> <img src="https://i.esdrop.com/d/fha5flk1blzo/rXY5GFUMd5.png" width="80%" align="center"> </p>
<p align="center">  <b> 그림 2. </b> 시각화에 사용할 화장품 정보 데이터셋. </p>

<br>

### 연구방법

<br>

#### 제품별 리뷰 수 Top N

1. 리뷰 수(review_count)를 제품명(product_name)과 함께 내림차순으로 정렬 후, 인덱스를 재정렬한다. 
2. plotly.express의 bar 그래프 함수를 이용해 막대 그래프를 그린다.
3. 특정 제품의 리뷰 수가 지나치게 많은 경우가 있으므로, y축에 log 스케일을 적용하는 것이 좋다.
4. 그래프 선언 후, update 기능을 이용해 그래프 세부사항을 업데이트해준다.
5. 그래프를 app.layout에 dcc.Graph 변수로 할당 후 결과를 확인한다.



