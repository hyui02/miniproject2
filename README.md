# ESAA YB 미니프로젝트 2 — 와인 품질 분류

DACON 와인 품질 분류 데이터로 와인의 품질 등급(3~9)을 분류한다. 평가 지표는 정확도이며, 최종 리더보드 점수는 **0.713**이다.

## 파일

| 파일 | 내용 |
|---|---|
| [`ESAA_YB_wine_quality_all.ipynb`](ESAA_YB_wine_quality_all.ipynb) | 데이터 확인부터 EDA, 전처리 결정, 검증 설계, 모델 비교, 앙상블, 시행착오, 최종 모델까지 전체 과정 |
| [`submission/submission_0712.csv`](submission/submission_0712.csv) | 리더보드 0.713 제출 파일 |
| [`requirements.txt`](requirements.txt) | 실행 환경의 라이브러리 버전 |

## 흐름

1. 데이터 구조, 중복 데이터, 품질 분포, 학습·테스트 비교, 변수 분포, 상관, 레드·화이트 비교, 등급별 차이
2. 전처리 결정(중복 유지, 불균형 처리 안 함, 결합 이산화황 추가), 중복을 고려한 검증 설계
3. 분류 모델 3종(Extra Trees, 랜덤 포레스트, XGBoost), 앙상블(리더보드 0.709), 0.709 이후의 정체와 원인
4. 트리와 원리가 다른 TabICL을 더한 최종 모델(리더보드 0.713), 종합

## 실행

Apple 칩 맥북에서 아래 순서로 실행했다. 데이터는 노트북이 처음 실행될 때 내려받는다. 전체 실행에 약 30분이 걸린다.

```bash
brew install libomp
python3.14 -m venv .venv
.venv/bin/pip install -r requirements.txt notebook
.venv/bin/jupyter notebook
```

트리 모델의 학습 계산은 CPU 종류에 따라 미세하게 달라지므로, Intel 계열 CPU(예: Google Colab)에서는 최종 예측의 몇 행이 바뀔 수 있다.
