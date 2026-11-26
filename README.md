# 부산 전·월세 실거래 공간 분석

2025년 부산 아파트 전·월세 실거래 자료를 자치구·월별로 집계하고 지도와 인터랙티브 차트로 비교한 프로젝트입니다. 3시간 시험에서 작성한 분석을 바탕으로 정리했으며, 당시 작성하지 않은 분석을 원래 성과로 추가하지 않았습니다.

## 분석 질문

- 자치구별 전세 보증금과 월세 수준은 어떻게 다른가?
- 거래 면적을 함께 고려하면 지역별 비교가 어떻게 달라지는가?
- 월별 변화와 보증금·월세·면적의 관계를 어떻게 시각화할 수 있는가?

## 데이터와 분석 과정

국토교통부 실거래 공개 자료를 저장한 Excel과 부산 행정구역 GeoJSON을 사용합니다. Excel의 계약년월로 2025년을 선택하고, 보증금·월세·면적을 숫자로 변환한 뒤 결측값과 면적0 이하를 제외합니다. 자치구별 평균과 월별 집계를 만들고 Folium·Plotly·Altair로 시각화했습니다.

현재 `면적당보증금`은 **구별 평균 보증금 ÷ 구별 평균 면적**입니다. 개별 거래의 ㎡당 가격을 평균한 값과 다르므로 지표를 혼동하지 않습니다. 주택 구성·보증금 수준·계약 시점 등을 통제한 인과 분석이나 가격 예측 모델은 아닙니다.

## 결과물

| 결과 | 파일 |
|---|---|
| 자치구별 전세 보증금 지도 | [Folium HTML](outputs/maps/2025_busan_jeonse_choropleth.html) |
| 월별 전세 보증금 변화 | [Plotly HTML](outputs/charts/2025_jeonse_slider.html) |
| 월별 월세 수준 | [3차원 Plotly HTML](outputs/charts/2025_wolse_3d.html) |
| 월세 변수 간 상관관계 | [Altair HTML](outputs/charts/2025_wolse_corr_heatmap.html) |
| 집계 자료 | [전세 CSV](outputs/tables/2025_gu_jeon.csv) · [월세 CSV](outputs/tables/2025_gu_wol.csv) |

GitHub 파일 화면에서는 HTML이 실행되지 않을 수 있습니다. 저장소를 내려받아 HTML 파일을 브라우저로 열면 상호작용할 수 있습니다.

## 구조와 실행

```text
busan-rent-choropleth_code.ipynb   전처리·집계·시각화
data/raw/                        기존 실거래 Excel
data/geo/                        부산 행정구역 GeoJSON
outputs/maps/ · charts/ · tables/ 지도·차트·집계표
```

```bash
python -m venv .venv
source .venv/bin/activate
pip install pandas numpy folium altair plotly openpyxl jupyterlab
jupyter lab busan-rent-choropleth_code.ipynb
```

저장소 루트에서 실행합니다. 원본 노트북의 분석 순서와 결과물은 보존했으며 로컬 고정 경로는 작업 디렉터리 기준으로 변경했습니다. 원본 Excel의 같은 집계식으로 전세26,679건·월세22,793건, 각각16개 자치구의 저장 집계표가 일치함을 확인했습니다([집계 확인 기록](docs/aggregate-check.json)).

## 한계

표본 수·거래 구성 차이, 갱신/신규 계약, 해제 거래 등 추가 조건에 따라 해석이 달라질 수 있습니다. 월세와 전세를 동일 경제적 비용으로 환산하지 않았습니다. 기존 자료의 정확한 다운로드 시점과 GeoJSON 출처·이용 조건을 보강할 필요가 있습니다. 이번 정리는 집계 확인과 문서 개선이며 전체 인터랙티브 화면을 새로 검증했다는 뜻은 아닙니다.
