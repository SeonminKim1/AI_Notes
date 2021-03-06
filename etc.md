■ 4대 인공지능 유명 학자 
- 제프리 힌튼 딥러닝 / 레이 커즈와일 / 얀 르쿤 박사 / 앤드류 응

■ 듀얼부팅 (파티션 분할 및 win10 + ubuntu)
- https://jimnong.tistory.com/676
- http://blog.dalli.kr/archives/1414 

■ pip vs pip3 vs anaconda
- (1) 일반 터미널에서의 pip 비교
  - 일반 cmd의 python pip (해당 python 에서 관리하는 전역 pip)
  - 일반 cmd의 python pip2, pip3 (local내에 pip2 버전에서 들어가지게 됨)
  
- (2) anaconda 가상환경 내에서 에서의 pip 비교
  - pip : 가상환경 안에 / pip2, pip3 : 로컬 전역에

- (3) conda install vs pip install 
  - conda install, pip install 모두 동일 / 속도적인 차이 있는 경우 있음


■ bias란
- 해당 뉴런이 본질적으로 가지고 있는 값

■ Backpropagation이란 
- weight와 bias를 조정하여 loss, cost을 줄이는 것.

■ 퍼셉트론 -> 다중 퍼셉트론 -> 신경망으로
- 오차 역전파를 통해 각 층의 가중치를 수정하려 하는데 층이 늘어나면서 기울기가 중간에 0이 되어 버리는 현상이 발생해 버렸음. (기울기 소실 – Vanishing gradient ) 
- 기울기 소멸문제는 은닉층이 많은 신경망에서 입력층에 가까운 층의 오차함수 E의 gradient가 영벡터(zero vector)에 가까워 지면서 발생함. -> 학습이 제대로 이루어지지 않게 되고 RELU와 같은 함수 선택
- 이는 활성화 함수인 시그모이드 함수 때문에 (시그모이드 함수는 미분하면 최대치가 0.3임, 1보다 작으니까 계속 곱하다 보니 0에 가까워 져버림) 가중치를 수정하기가 어려워지고 다른 활성화 함수를 대체하게 됨.

■ 가중치 초기화 문제 (Weight Initialize)
- 신경망의 성능에 큰 영향을 주는 요소
- 보통 가중치의 초기값으로 0에 가까운 무작위 값을 사용하였음. 
- 이것을 개선하고자 가중치 초기화 다양한 방법이 논의됨.
- (1) 균등분포 
- (2) 제이비어 초기화(Xavier)에서 무작위 선택 /  N(0,1) 표준 정규분포
- (3) 허(He) 초기화에서 무작위 선택
- (4) batch normalization이 나온 이후 .. 사라짐

■ LRN (Local response normalization)
- 활성화 된 뉴런이 주변 이웃 뉴런들을 억누르는 현상(lateral inhibition)을 모델링 한 것으로, 강하게 활성화 된 뉴런의 주변 이웃들에 대해서 normalization을 실행한다. 주변에 비해 어떤 뉴런이 비교적 강하게 활성화 되어 있다면, 그 뉴런의 반응은 더욱더 돋보이게 될 것. 반면 강하게 활성화 된 뉴런 주변도 모두 강하게 활성화 되어 있다면, local response normalization이후에는 모두 값이 작아질 것이다.

■ Normalization vs Standardization
- Normalize나 Standardize는 모두, 모든 데이터를 같은 scale로 만들어주는 것이 목적
- feature들은 같은 Scale을 가지고 있지 않은 non-Normalized한 상태이다. 이러한 data는 Neural Network에서 불안정함을 야기하므로, 너무 큰 범위의 feature값이 들어가게 되면, gradient를 태워 weight를 업데이트 할 때 큰 문제가 발생하게 된다.
- Normalization : 구체적으로 10 ~ 1000 범위를 가진 feature를 0~1값을 가지도록 Scaling함
- Standardization : 각 데이터에 평균을 빼고 -> 표준편차로 나눠서 -> 평균0 표준편차 1인 데이터로 변형 
- 0에서 1사이로 정규화 하냐 vs 평균이 0으로 되도록 표준화 하냐 차이.

ex) 데이터를 Neural Network에 train시키기 전에 preprocessing을 통해 Normalize 또는 Standardize를 했다.
