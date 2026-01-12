# Busan Rent Choropleth (2025)

부산광역시 전·월세 실거래 데이터를 전처리하여 구별 ㎡당 전세 보증금/월세 수준을 계산하고,
Folium Choropleth + Plotly/Altair로 시각화한 프로젝트입니다.
(3시간 시험동안 작성한 코드를 깃허브에 배포할 수 있게 만든 것으로, 시험시간동안 작성되지 않은 그래프는 담지 않았습니다.)

Repository Structure

busan-rent-choropleth_code.ipynb : 전체 분석/시각화 노트북

data/geo/ : 부산 행정구역 GeoJSON

data/raw/ : 원본 데이터(엑셀)

outputs/

maps/ : Folium 지도 HTML

charts/ : Plotly/Altair HTML

tables/ : 구별 집계 CSV

# How to Run

(권장) 가상환경 생성 후 패키지 설치

pip install pandas numpy folium altair plotly openpyxl

Jupyter에서 노트북 실행

busan-rent-choropleth_code.ipynb

Outputs

outputs/maps/2025_busan_jeonse_choropleth.html

outputs/charts/2025_jeonse_slider.html

outputs/charts/2025_wolse_3d.html

outputs/charts/2025_wolse_corr_heatmap.html

outputs/tables/2025_gu_jeon.csv

outputs/tables/2025_gu_wol.csv

Data Source

행정구역 GeoJSON: 공개 GitHub 기반 행정동 경계 자료
전월세 실거래가: 국토교통부 공개 api 자료
