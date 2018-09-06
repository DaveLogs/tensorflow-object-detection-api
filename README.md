# Tensorflow Object Detection API

Tensorflow Object Detetion API는 Tensorflow를 이용하여 이미지를 인식할 수 있도록 하는, 각기 다른 정확도와 속도를 갖는 5개의 모델을 라이브러리 형태로 제공하는 오픈소스 프레임워크이다. 본 문서는 Tensorflow Object Detection API를 사용할 수 있는 환경을 구축하는 방법을 설명한다.

본 문서에서 진행할 설치 과정의 환경은 다음과 같다.

- Operating System : Linux
- Architecture : x86_64
- Distribution : Ubuntu 16.04.5
- Virtual Environment : virtualenv
- Python Version : Python 3.5.2
- Tensorflow Version : Tensorflow 1.10.1

참고로 위와 같은 환경은 https://github.com/deokheon/tensorflow-gpu-install-on-ubuntu-16.04/blob/master/README.md 문서를 참고하기 바란다.

이제부터 진행하게 될 설치 과정은 다음과 같다.

1. 설치
2. 테스트
3. 사용하기

---
## STEP 1: 설치

Tensorflow Object Detection API를 이용하기 위해 필요한 주요 설치 항목은 다음과 같다.

* Protobuf 3.x
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

## Library 설치


---
## 참고

Tensorflow Object Detection 원본 설치 문서 : https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/installation.md
