#인적사항<br>
이름 : 김태완<br>
학년 : 3학년<br>
학과 : 컴퓨터공학부<br>
학번 : 201912049<br>
분반 : 금요일(6,7,8)<br>
<hr>
<br>
##참고사항<br>
코드를 수정하는 방법에 어려움을 겪어 ChatGPT와 다양한 블로그 글의 도움을 받아 작성하였습니다.
<br>
Readme를 작성해본적이 없어 가독성이 떨어지는 점 죄송합니다.<br>
<hr>
##1번 수정<br>
<img src = "https://github.com/programofktw/OpenSW_Balloon/assets/100819044/8f2c9228-1220-493c-913b-e6876b441a79">
<br>
수정 내용 : tensorflow2.x로 버전이 업그레이드 되면서 tensorflow에 keras와 tensorflow-gpu가 통합됨.
tensorflow-gpu의 경우 사용하기 위해서는 Nvidia 그래픽 카드가 필요한데
노트북 내장 그래픽이 Intel이라 GPU버전은 사용하지 못함
<br>
keras같은 경우 tensorflow에 내장된 패키지로 사용하기 위해서
keras.x들을 위의 사진처럼
tensorflow.keras.x로 변경
<hr>
##2번 수정<br>
<img src = "https://github.com/programofktw/OpenSW_Balloon/assets/100819044/b9c7fc8d-4dad-4c37-bfc9-5fc803065615">
<br>
수정 내용 : tensorflow2.x로 버전이 업그레이드 되면서 tensorflow에 패키지 디렉토리가 달라져서
log를 사용하기 위해서는 tf.log를 tf.math.log로 변경해야함.
<hr><br>
##3번 수정<br>
<img src = "https://github.com/programofktw/OpenSW_Balloon/assets/100819044/7417d241-8001-4b08-a6bd-0a46e0b2d9ac">
<br>
<img src = "https://github.com/programofktw/OpenSW_Balloon/assets/100819044/70300d1e-1b35-4c82-b949-4edb920dd8d2">
<br>
수정 내용 : tensorflow2.x로 버전이 업그레이드 되면서 tensorflow1.x버전의 메소드들을 기본적으로는 쓸 수 없어서
실행을 시킬때마다 오류가 생김.<br>
이를 위해서 tensorflow1.x 버전의 메소드들을 tensorflow2.x버전에서도 사용할 수 있게 하기 위해서
tf.compat.v1 을 통해 호환성을 맞춰줌.
<br>
이 수정은 코드 전반에 걸쳐서 이루어지고 있기때문에 전부 서술하는 것이 아닌 2개 정도만 서술해둠.

<hr>
##4번 수정<br>
<img src = "https://github.com/programofktw/OpenSW_Balloon/assets/100819044/92ad43da-dc05-47ba-85d3-b91493fe7e11">
<br>
수정 내용 : 본래 깃허브 코드의 경우 index 유효성 검사를 위한 메소드를 사용하는데 이것에서 계속해서 오류가터짐.
<br>
해당 오류를 고치는 방법을 알 수 없어서, index 유효성 검사를 하지 않는 메소드로 변경하여 작성
<hr>
##5번 수정<br>
<img src = "https://github.com/programofktw/OpenSW_Balloon/assets/100819044/f3366161-85d1-47e5-9c16-0d4d36ee658a">
수정 내용 : KL.Reshape 메소드가 과거 github 코드에서는 문제가 없었지만 2.x버전으로 넘어오면서 오류가 생김.
tensor를 생성할때 s[1]에 들어가는값이 들어가지 않아서 문제가 생기기 떄문이라고 확인을 하였음.
<br>
해당 문제를 해결할 방법을 찾지 못했지만 인터넷 서치 결과
s[1]가 None일때 -1을 대신 집어 넣으면 가능하게 함으로 써 해결.
<hr>
##6번 수정<br>
<img src = "https://github.com/programofktw/OpenSW_Balloon/assets/100819044/55e166de-d082-4f15-b877-fb13b90d11db">
수정 내용 : 본래 공식 github 코드에는 use_mini_mask 값이 오류를 터트리는 것을 확인하였음.
이를 해결하기 위해서 애초에 해당 메소드에서 파라미터로써 이를 제거함.
그로인해 분명 영향이 있었을텐데 이는 확인하지 못함.
<br>
<br>
<hr>
##실행 과정<br>
아나콘다 환경 제작<br>
conda create --name (환경명) python=3.7 pip
<br>
#python 3.7가 아니면 작동이 정상적으로 안됨.<br>
#3.7중에서도 3.7.16으로 진행함<br>
pip install tensorflow<br>
pip install pip install scikit-image<br>
python balloon.py --dataset ../../model/balloon/datasets --weights ../../mask_rcnn_balloon.h5 --logs ../../model/balloon/logs --image ../../model/balloon/datasets/val/3800636873_ace2c2795f_b.jpg splash<br>
