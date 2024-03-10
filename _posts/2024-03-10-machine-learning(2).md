---
layout: single
categories: AI/딥러닝
tag: 머신러닝
title: "머신러닝(2) - 패턴인식 알고리즘의 성능평가"
typora-root-url: ../
tos: true
---

패턴인식 알고리즘을 **평가하는 방법은 다양**하지만, 가장 일반적인 방법 중 하나는 **혼동행렬(Confusion matrix)**을 사용하여 **정확도(오류율)**를 평가하는 것입니다.

![image-20240310220224822](/images/2024-03-10-machine-learning(2)/image-20240310220224822.png)

- **Actual Positive, Actual Negative:** 실제 값들
- **TP:** 실제 Positive 값을 Positive로 맞게 인식한 값 / **TN:** 실제 Negative 값을 Negative로 맞게 인식한 값
- **FN:** 실제 Positive 값을 Negative로 틀리게 인식한 값 / **FP:** 실제 Negative 값을 Positive로 틀리게 인식한 값

- **Precision:** <u>Positive라고 인식된 값</u>들 중에 실제 Positive 값은 얼마나 되는지 비율로 표현한 값
- **Recall:** <u>실제 Positive 값</u>들 중에 positive로 인식한 값을 비율로 표현한 값



**ROC(Receiver Operating Characteristic)곡선**

![image-20240310221822793](/images/2024-03-10-machine-learning(2)/image-20240310221822793.png)

- 임계값 이상의 데이터 중에서 본인 점수 분포를 TAR(True Accept Rate), 사칭자 점수 분포를 FAR(False Accept Rate)
- 분홍색: TNR / 파란색: FNR / 초록색: TPR / 주황색: FPR=FAR

임계값을 조정함에 따라 패턴인식 시스템의 성능이 변화합니다. 일반적으로, 패턴인식에서 임계값은 TAR(True Accept Rate, 정확히 인식된 비율)과 FAR(False Accept Rate, 잘못된 인식 비율)를 결정하는 데 중요한 역할을 합니다.

임계값을 높이면 FAR이 줄어들지만, 그만큼 TAR도 감소합니다. 반대로, 임계값을 낮추면 TAR이 증가하지만, FAR도 증가합니다. 이러한 임계값의 조정은 패턴인식 시스템의 성능을 결정짓는 중요한 요소 중 하나입니다.

임계값의 변화에 따른 성능을 시각화하기 위해 ROC(Receiver Operating Characteristic) 곡선을 그릴 수 있습니다. ROC 곡선은 임계값을 변화시킬 때 TAR과 FAR의 변화를 보여줍니다.

따라서 패턴인식 시스템을 평가하고 개선하기 위해서는 임계값에 대한 적절한 조정과 ROC 곡선의 분석이 필요합니다.



**AUROC(Area Under ROC)**

![image-20240310223140849](/images/2024-03-10-machine-learning(2)/image-20240310223140849.png)

ROC 곡선의 좌상 꼭지점에 가까울수록 면적이 넓으므로, 인식 알고리즘이 우수하다고 평가할 수 있습니다. 면적이 넓을수록 동일한 TAR 대비 FAR이 작고, 동일한 FAR 대비 TAR이 작아지기 때문입니다. 따라서 초록색 시스템이 빨간색 시스템보다 성능이 높다고 평가할 수 있습니다.

