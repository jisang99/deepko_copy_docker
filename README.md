# deepko

**deepko** (**DEEP** learning docker for **KO**rean) 는 <u>파이썬(Python) 기반의 데이터 분석 / 머신러닝 / 딥러닝 도커(docker)</u> 입니다.

- 파이썬 기반의 데이터 분석, 머신러닝, 딥러닝 프레임워크의 상호 의존성 충돌을 해결 후 배포합니다.

- **한글 폰트, 한글 자연어 처리(형태소 분석기)** 를 위한 라이브러리가 사전에 설치되어 있습니다.

- **GPU** 를 지원합니다 (`LightGBM`, `XGBoost`, `PyTorch`, `TensorFlow`).

- 도커를 통한 빠른 설치와 실행이 가능합니다.
  

## 개요

TensorFlow 의 [tensorflow/tensorflow:2.12.0rc1-gpu-jupyter](https://hub.docker.com/layers/tensorflow/tensorflow/2.12.0rc1-gpu-jupyter/images/sha256-38561c1cb2829316ca7b8e0396608e4c2b383a6fdf1411e79f7257f1d35bd204?context=explore)의 도커를 베이스로 확장하여 GPU 전용 Docker파일(`gpu.Dockerfile`)을 구성하였습니다. 

TensorFlow에서 유지보수하고 있는 `2.12.0rc1-gpu-jupyter` 도커의 경우 한글 형태소 분석기나 한글폰트, 그 밖에 PyTorch를 비롯한 여러 머신러닝/딥러닝 라이브러리가 제외되어 있기 때문에 필요한 라이브러리를 추가 설치하고 의존성에 문제가 없는지 확인한 후 배포하는 작업을 진행하고 있습니다.

본 Repository를 만들게 된 계기는 안정적으로 업데이트 되고 있는 `tensorflow/tensorflow-gpu-jupyter`에 기반하여 한글 폰트, 한글 자연어처리 패키지(konlpy), 형태소 분석기(mecab), Timezone 등의 설정을 추가하여 별도의 한글 관련 패키지와 설정을 해줘야 하는 번거로움을 줄이기 위함입니다.

- **GPU** 버전 도커 **Hub** 주소: [teddylee777/deepko](https://hub.docker.com/repository/docker/teddylee777/deepko)
- **GitHub** 주소: [github.com/teddylee777/deepko](https://github.com/teddylee777/deepko)



## 테스트된 도커 환경

- OS: Ubuntu 20.04
- GPU: RTX3090 x 2 way
- **CUDA: 11.8** (2023년 03월 18일 업데이트)
- Python (anaconda): 3.8

## CUDA 11.8 업데이트 방법

링크: https://teddylee777.github.io/linux/ubuntu2004-cuda-update/

## 업데이트 내역

업데이트 내역: https://github.com/teddylee777/deepko/wiki/%EB%B2%84%EC%A0%84-%EC%97%85%EB%8D%B0%EC%9D%B4%ED%8A%B8


## 한글 관련 추가 패키지

- apt 패키지 인스톨러 카카오 mirror 서버 추가
- Nanum(나눔) 폰트, D2Coding 폰트 설치
- matplotlib 에 나눔폰트, D2Coding 폰트 추가
- mecab 형태소 분석기 설치 및 파이썬 패키지 설치
- [konlpy](https://konlpy-ko.readthedocs.io/ko/v0.4.3/): 한국어 정보처리를 위한 파이썬 패키지
- `jupyter_notebook_config.py` : Jupyter Notebook 설정 파일 추가



## 설치된 주요 라이브러리

```
catboost                     1.1.1
cmake                        3.26.0
fastai                       2.7.11
fasttext                     0.9.2
folium                       0.14.0
gensim                       4.3.1
graphviz                     0.20.1
huggingface-hub              0.13.2
hyperopt                     0.2.7
jupyterlab                   3.6.1
kaggle                       1.5.13
keras                        2.12.0rc1
konlpy                       0.6.0
librosa                      0.10.0.post2
lightgbm                     3.3.5
matplotlib                   3.7.1
mecab-python                 0.996-ko-0.9.2
missingno                    0.5.2
mlxtend                      0.21.0
notebook                     6.5.3
numpy                        1.23.5
opencv-python                4.7.0.72
optuna                       3.1.0
pandas                       1.5.3
plotly                       5.13.1
prophet                      1.1.2
pyfasttext                   0.4.6
PyMySQL                      1.0.2
QtPy                         2.3.0
scikit-image                 0.20.0
scikit-learn                 1.2.2
scipy                        1.9.1
seaborn                      0.12.2
sentencepiece                0.1.86
soynlp                       0.0.493
soyspacing                   1.0.17
spacy                        3.5.1
SQLAlchemy                   2.0.6
tensorboard                  2.12.0
tensorflow                   2.12.0rc1
tensorflow-datasets          4.8.3
tokenizers                   0.13.2
torch                        2.0.0+cu118
torchaudio                   2.0.1+cu118
torchdata                    0.6.0
torchsummary                 1.5.1
torchtext                    0.15.1
torchvision                  0.15.1+cu118
transformers                 4.27.1
wandb                        0.14.0
wordcloud                    1.8.2.2
xgboost                      1.7.4
```



## GPU 지원 라이브러리

다음의 라이브러리에 대하여 **GPU를 지원**합니다.

1. `LightGBM` (3.3.5)
2. `XGBoost` (1.7.4)
3. `PyTorch` (2.0.0) + CUDA 11.8
4. `TensorFlow` (2.12.0rc1) + CUDA 11.8



## 실행 방법

### STEP 1: Docker가 사전에 설치되어 있어야 합니다.

도커의 설치 및 사용법에 대하여 궁금하신 분들은 [Docker를 활용하여 딥러닝/머신러닝 환경 구성하기](https://teddylee777.github.io/linux/docker%EB%A5%BC-%ED%99%9C%EC%9A%A9%ED%95%98%EC%97%AC-%EB%94%A5%EB%9F%AC%EB%8B%9D-%ED%99%98%EA%B2%BD%EA%B5%AC%EC%84%B1.md) 글을 참고해 주세요.

```bash
# step 1: apt-get 업데이트
sudo apt-get update

# step 2: 이전 버젼 제거
sudo apt-get remove docker docker-engine docker.io

# step 3: 도커(Docker) 설치 
sudo apt install docker.io

# step 4: 도커 서비스 시작
sudo systemctl start docker
sudo systemctl enable docker

# step 5: 잘 설치 되어있는지 버젼 체크
docker --version
```



### STEP 2: 도커 이미지 pull 하여 서버 실행

상황에 따라 다음 4가지 중 하나의 명령어를 실행하여 도커를 실행합니다. 세부 옵션은 아래를 참고해 주세요.

- `--rm`: 도커가 종료될 때 컨테이너 삭제

- `-it`: 인터랙티브 TTY 모드 (디폴트로 설정)

- `-d`: 도커를 백그라운드로 실행

- `-p`: 포트 설정. **local 포트:도커 포트**

- `-v`: local 볼륨 마운트. **local 볼륨:도커 볼륨**

- `--name`: 도커의 별칭(name) 설정

  

1. `Jupyter Notebook` 을 **8888번 포트로 실행**하려는 경우

```bash
docker run --runtime nvidia --rm -it -p 8888:8888 teddylee777/deepko:preview
```



2. `jupyter notebook` 서버 실행과 동시에 **로컬 volume 마운트**

```bash
docker run --runtime nvidia --rm -it -p 8888:8888 -v /data/jupyter_data:/home/jupyter teddylee777/deepko:preview
```



3. 도커를 **background에서 실행**하는 경우 (터미널을 종료해도 서버 유지)

```bash
docker run --runtime nvidia --rm -itd -p 8888:8888 teddylee777/deepko:preview
```



4. 도커를 실행 후 **bash shell로 진입**하려는 경우

```bash
docker run --runtime nvidia --rm -it -p 8888:8888 teddylee777/deepko:preview /bin/bash
```



**[참고]**

`jupyter_notebook_config.py` 을 기본 값으로 사용하셔도 좋지만, 보안을 위해서 **비밀번호 설정**은 해주시는 것이 좋습니다.

**비밀번호 설정** 방법, **방화벽 설정** 방법은 [Docker를 활용하여 딥러닝/머신러닝 환경 구성하기](https://teddylee777.github.io/linux/docker%EB%A5%BC-%ED%99%9C%EC%9A%A9%ED%95%98%EC%97%AC-%EB%94%A5%EB%9F%AC%EB%8B%9D-%ED%99%98%EA%B2%BD%EA%B5%AC%EC%84%B1.md) 글의 STEP 5, 7을 참고해 주세요.



## [선택] .bashrc에 단축 커멘드 지정

`~/.bashrc`의 파일에 아래 커멘드를 추가하여 단축키로 Docker 실행


```bash
kjupyter{
    docker run --runtime nvidia --rm -itd -p 8888:8888 -v /data/jupyter_data:/home/jupyter --name dl-ko teddylee777/deepko:preview
}
```

 위와 같이 `~/.bashrc` 파일을 수정 후 저장한 뒤 `source ~/.bashrc`로 파일의 내요을 업데이트 합니다.

추후, 긴 줄의 명령어를 입력할 필요 없이 단순하게 아래의 명령어로 도커를 백그라운드에서 실행 할 수 있습니다.

```bash
kjupyter
```





---



**추가 파이썬 패키지 설치 제안은 issue 에 남겨주세요!**

감사합니다.
