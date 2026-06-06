**1. PyTorch란?**  
- 딥러닝 신경망 구축을 위한 오픈소스 프레임워크  
- Torch 머신러닝 라이브러리 + Python API를 결합  
- 쉽고 직관적인 문법을 제공하며, 동적 연산이 가능  

**2. PyTorch vs TensorFlow 비교**  
| 항목 | PyTorch | TensorFlow |
| :---: | :---: | :---: |
| 개발사 | Meta (Pytorch Foundation) | Google |
| 주요 사용처 | 연구, 학계 | 산업, 제품 배포 |
| 장점 | 사전 학습 모델과 문서가 많음 | Google 서비스와 통합 용이 |

**3. PyTorch 저장소 및 사용자 현황**  
- GitHub 및 Hugging Face에서 활발하게 사용됨  
- 연구 커뮤니티에서 선호되며, TensorFlow보다 학습 용이성에서 강점  

**4. PyTorch 사용법**  
**:closed_book: 텐서 (Tensor)**  
- PyTorch의 핵심 데이터 구조  
- NumPy 배열과 유사하지만 GPU 가속이 가능  

**:closed_book: PyTorch 자료형**  
- torch.FloatTensor → 32비트 실수형 텐서  
- torch.IntTensor → 32비트 정수형 텐서  
- torch.cuda.FloatTensor → GPU 가속된 실수형 텐서  

:book: 요약 정리  
- PyTorch는 **컴퓨터 비전, 자연어 처리, 강화 학습** 등 다양한 AI 분야에서 활용되는 딥러닝 프레임워크  
- TensorFlow와 비교했을 때, PyTorch는 동적 연산과 문법이 더 직관적  
- Hugging Face와 같은 플랫폼에서 사전 학습 모델을 쉽게 활용 가능
```
https://huggingface.co/
```
- 텐서(Tensor)는 PyTorch의 핵심 자료형이며, GPU 가속 지원

**:white_check_mark: 경사하강법 (Gradient Descent)** 
:bulb: 손실(Loss)을 최소화하기 위해 파라미터를 조정하는 알고리즘  
- 모델이 **손실이 줄어드는 방향(기울기의 음의 방향)**으로 이동하며 학습  
**:small_blue_diamond: 핵심 절차**  
1. 예측 계산 → `Yp = W * X + B`  
2. 손실 계산 → `(Yp - Y)²` 평균(MSE)  
3. 경사 계산 → `loss.backward()` (자동미분)  
4. 파라미터 수정 → `W -= lr * W.grad`  
5. 경사 초기화 → `optimizer.zero_grad()`  

**:gear: Optimizer (최적화 함수)**  
- torch.optim.SGD, Adam 등으로 파라미터 자동 업데이트  
- Momentum 사용 시 빠르고 안정적인 수렴  
- 학습률(lr) 조절이 핵심: 너무 크면 발산, 너무 작으면 수렴 지연  

**:white_check_mark:오차역전파(Backpropagation)**  
- 신경망 학습의 핵심 알고리즘으로, 손실(loss)을 최소화하기 위해 가중치를 조정하는 과정  
- 미분을 이용해 오차를 역으로 전달하여 가중치를 업데이트함  


**:white_check_mark:활성화 함수(Activation Function)**  
- 뉴런의 출력을 결정하는 함수로, 비선형성을 추가하여 신경망이 복잡한 패턴을 학습할 수 있도록 함  
- 주요 활성화 함수:  
  ◦ **ReLU(Rectified Linear Unit)**: 기울기 소실 문제 해결, 대부분의 딥러닝 모델에서 사용  
  ◦ **Sigmoid**: 0~1 사이 값 출력, 이진 분류 문제에 사용됨  
  ◦ **Tanh**: -1~1 사이 값 출력, Sigmoid보다 성능이 좋지만 깊은 신경망에서는 기울기 소실 가능  
















