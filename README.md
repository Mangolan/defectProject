'''
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
'''
![프로필 이미지](./wide_resnet50_2_architecture.png)
