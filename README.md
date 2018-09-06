# Tensorflow Object Detection API

Tensorflow Object Detetion API는 Tensorflow를 이용하여 이미지 속 를 인식할 수 있도록 하는, 각기 다른 정확도와 속도를 갖는 5개의 모델을 라이브러리 형태로 제공하는 오픈소스 프레임워크이다. 본 문서는 Tensorflow Object Detection API를 사용할 수 있는 환경을 구축하는 방법을 설명한다.

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

* protobuf 3.x
* python-tk
* pillow 1.0
* lxml
* jupyter notebook
* matplotlib
* cython
* contextlib2

### Protocol Buffer 설치

```
# Make sure you grab the latest version
$ curl -OL https://github.com/google/protobuf/releases/download/v3.6.1/protoc-3.6.1-linux-x86_64.zip

# Unzip
$ unzip protoc-3.6.1-linux-x86_64.zip -d protoc3

# Copy protoc to /usr/local/bin/
$ sudo cp protoc3/bin/* /usr/local/bin/

# Copy protoc3/include to /usr/local/include/
$ sudo cp -r protoc3/include/* /usr/local/include/
```

### Library 설치

```
$ sudo apt-get install python-pil python-lxml python-tk
```

```
(venv) $ pip install Cython
(venv) $ pip install contextlib2
(venv) $ pip install jupyter
(venv) $ pip install matplotlib
(venv) $ pip install pillow
(venv) $ pip install lxml
```

---
## STEP 2: 테스트

### Clone Tensorflow Models
Tensorflow Object Detection API가 포함된 오픈소스를 다운로드한다.

```
$ mkdir -p /workspace/tensorflow
$ cd /workspace/tensorflow
$ git clone https://github.com/tensorflow/models
```

### Protobuf Compilation
Protocol Buffer를 사용하기 위해 .proto 파일을 컴파일한다.

```
$ cd /workspace/tensorflow/models/research
$ protoc object_detection/protos/*.proto --python_out=.
```

### PYTHONPATH 설정

환경변수에 모델이 존재하는 경로를 추가해 주는 과정으로, shell이 실행될 때마다 해 주어야 한다.
```
# From tensorflow/models/research/
(venv) $ cd /workspace/tensorflow/models/research
(venv) $ export PYTHONPATH=$PYTHONPATH:`pwd`:`pwd`/slim:`pwd`/object_detection
```

단, 아래와 같이 .bashrc에 관련 경로를 추가해 놓으면 편하다. 
```
$ echo -e '\n## PYTHONPATH settings for tensorflow object detection' >> ~/.bashrc
$ echo 'export PYTHONPATH=$PYTHONPATH:/workspace/tensorflow/models/research:/workspace/tensorflow/models/research/slim:/workspace/tensorflow/models/research/object_detection' >> ~/.bashrc
```

### Testing the installation
```
(venv) $ cd /workspace/tensorflow/models/research
(venv) $ python object_detection/builders/model_builder_test.py
.........
------------------------------------------------------------------
Ran 18 tests in 0.059s

OK
```

## STEP 3: 사용하기
설치가 끝났으니 테스트용 노트북 파일을 통해 실제로 이미지 속 객체가 인식되는 것을 확인해 본다.

```
(venv) $ cd /workspace/tensorflow/models/research
(venv) $ jupyter notebook
```

웹브라우저에서 localhost:8888/tree가 열리면, object_detection 디렉토리 내에 object_detection_tutorial.ipynb를 열어 실행시켜 보면 다음과 같이 인식한 결과가 나올 것이다.



---
## 참고

Tensorflow Object Detection 원본 설치 문서:
https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/installation.md

