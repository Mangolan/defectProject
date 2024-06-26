# Wide Resnet 모델 설명
~ 기본 개념
ResNet (Residual Network)은 딥러닝에서 매우 깊은 네트워크를 효과적으로 훈련할 수 있도록 설계된 구조입니다. 이 모델은 잔차 연결(residual connections)을 통해 입력을 레이어의 출력에 직접 더해주어, 깊은 네트워크에서 발생할 수 있는 소실된 기울기(vanishing gradient) 문제를 해결합니다.
```
import torch
from torchviz import make_dot
from torchvision.models import wide_resnet50_2, Wide_ResNet50_2_Weights

def main():
    # 모델 로드, 사전 훈련된 가중치 사용
    model = wide_resnet50_2(weights=Wide_ResNet50_2_Weights.IMAGENET1K_V1)
    # 더미 입력 데이터
    x = torch.randn(1, 3, 224, 224)
    # 모델 실행
    y = model(x)
    # 계산 그래프 시각화
    dot = make_dot(y, params=dict(list(model.named_parameters())))
    # 이미지 파일로 계산 그래프 저장
    dot.render("wide_resnet50_2_architecture", format="png")

if __name__ == '__main__':
    main()
```
![프로필 이미지](./wide_resnet50_2_architecture.png)
