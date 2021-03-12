# How-to-install-tensorflow-on-Windows

Environment: Anaconda
OS: Windows 10 64bit

[아나콘다 관련]
1. 아나콘다를 설치한 이후, "Anaconda Prompt" 또는 "Anaconda Powershell"을 "**관리자권한**"으로 실행하여 커맨드 창을 띄움.
2. 아나콘다 자체 업데이트 : 
* conda update -n base -c defaults conda
3. 아나콘다에서 가상환경 생성 : 
* conda create -n tfgpu python=3.7 -y
* 여기서 tfgpu는 가상환경이름이며, 본인 원하는 대로 지어도 상관없음. 이후 tfgpu는 본인이 생성한 가상환경이름이라 가정함.
* 주의사항 : 아나콘다를 2021년 이후로 새로 받을 경우, 가상환경 생성시 기본 파이썬 버전이 3.8 혹은 그 이상의 버전이 될 수 있음. 이는 추후 tensorflow-gpu 설치에 영향을 줄 수 있으므로, 위에서처럼 별도로 파이썬 버전을 설정하는 것이 필요.
* 파이썬 버전은 3.6이나 3.5처럼 낮춰도 됨.
4. 방금 생성한 가상환경을 활성화시키고 그 안에서 설치하기 :
* conda activate tfgpu

[본격적으로 텐서플로우 GPU 설치하기]
1. 아나콘다 패키지를 활용한 간단한 텐서플로우 GPU 설치하기
* conda install -c anaconda tensorflow-gpu
* 주의사항 : 2021년 2월 기준으로 윈도우10 64비트용 최신 GPU 버전은 2.3.0임. 
* 만약 아나콘다 클라우드에서 GPU버전을 업데이트할 경우, 위 명령어는 보다 상위버전으로 설치할 수 있음.
* 특정 GPU 버전으로 설치하고 싶을 경우 : conda install -c anaconda tensorflow-gpu==2.3.0
2. cuDNN 및 CUDA가 제대로 설치되었는지 확인하기
* conda list -n tfgpu
* 위 명령어를 치고, 가장 왼쪽열에서 cudnn과 CUDA 이름 있는지 확인해보기.
* 없는 경우, 가상환경 다시 만들고 파이선버전을 다운그레이드하는 것이 좋음. 혹은 TF-GPU버전도 다운된 것으로 명시하는 것 필요(예컨대 2.1.0). 

[텐서플로우 GPU 설치 확인작업]
1. python 타입핑
2. import tensorflow 타입핑
3. print(tensorflow.__version__) 타입핑
4. 버전(예컨대 2.1.0)이 출력되면 정상 설치된 것임.


[기타 참고]
1. 딥러닝/머신러닝에 종종 사용되는 라이브러리를 한 번에 설치하고 싶은 경우
* conda install numpy scipy matplotlib pandas scikit-learn seaborn pydotplus python-graphviz -y
* 마지막의 "-y" 명령어를 사용하면 yes/no 확인 필요 없이 바로 설치 시작함. 이미 설치한 라이브러리가 있어서 버전 충돌이 우려되는 경우에는 "-y" 명령어를 지우고 설치하면 됨.
2. 쥬피터노트북 관련 참고사항
* conda install ipython notebook -y
* 쥬피너 노트북에 커널명 추가하기
* python -m ipykernel install --user --name tfgpu2 --display-name "[displayKenrelName]"
* 쥬피터 노트북의 시작경로 변경하기(지금만 반영됨)
* jupyter notebook --notebook-dir="C:/Your/Desired/Start/Directory/"
