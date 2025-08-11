# yolov5-deep-compression
yolo 학습 및 모델 경량화

📊 성능 비교
<img width="2155" height="938" alt="image" src="https://github.com/user-attachments/assets/b6adff26-d3c6-44b8-8712-823bc0673ced" />

# insstallation
# Python 3.8+ 필요
# 1. 저장소 클론
git clone https://github.com/yourusername/yolov5-deep-compression.git
cd yolov5-deep-compression

# 2. 필요 패키지 설치
pip install ultralytics
pip install scikit-learn scipy
pip install matplotlib seaborn

사용법
python yoloretrain.py
(yoloretrain 실행 후 생긴 pt 파일 경로 설정 후)
python compress.py

프루닝 - conv_threshold=0.005, fc_threshold=0.015, retrain_epochs=17, learning_rate=0.001 조절
threshold 값 커질수록 경량화 강도 커짐

양자화 - k값 조절 커질수록 경량화 강도 낮아짐
                    if isinstance(module, nn.Conv2d):
                        k = int(2.2 ** conv_bits)  # 256 for 8-bit
                        bits = conv_bits
                    else:
                        k = int(2.2 ** fc_bits)  # 32 for 5-bit
                        bits = fc_bits
