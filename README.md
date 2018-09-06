# Tensorflow Object Detection API

Tensorflow를 이용하여 이미지를 인식할 수 있도록 하는, 각기 다른 정확도와 속도를 갖는 5개의 모델을 라이브러리 형태로 제공한다.

본 문서에서는 진행할 설치 환경은 다음과 같다.

- Operating System : Linux
- Architecture : x86_64
- Distribution : Ubuntu 16.04.5
- Virtual Environment : virtualenv
- Python Version : Python 3.5.2
- Tensorflow Version : Tensorflow 1.10.1

이어서 본 문서에서 진행하게 될 과정은 다음과 같다.

1. 설치
2. 테스트
3. 사용하기

---
## STEP 1: 설치

Tensorflow Object Detection API를 이용하기 위해 필요한 주요 설치 항목은 다음과 같다.

* Protobuf 3.0.0
* Python-tk
* Pillow 1.0
* lxml
* jupyter notebook
* cython
* contextlib2

### Protocol Buffer 설치
```
# Make sure you grab the latest version
curl -OL https://github.com/google/protobuf/releases/download/v3.6.1/protoc-3.6.1-linux-x86_64.zip

# Unzip
unzip protoc-3.6.1-linux-x86_64.zip -d protoc3

# Copy protoc to /usr/local/bin/
sudo cp protoc3/bin/* /usr/local/bin/

# Copy protoc3/include to /usr/local/include/
sudo cp -r protoc3/include/* /usr/local/include/
```

---
## 참고

Tensorflow Object Detection 원본 설치 문서 : https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/installation.md
