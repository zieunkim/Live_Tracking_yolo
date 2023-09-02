# Live_Tracking_yolo


안녕하세요! SKT AI Fellowship에서 **Live Tracking** 과제를 연구하고 있는 *Team* **<span style="color: #0ac90b">금쪽이들</span>**입니다.

![](https://devocean.sk.com/editorImg/2022/11/30/6ea52f90b64a03fd9b477ba3655664167682d3566bc2d2e7638d8f833865014e)

## **Overview**

**Live Tracking** 과제는 1인 또는 소규모의 미디어 콘텐츠 제작자들을 위해, 고정된 카메라에서 피사체를 실시간으로 트래킹하여 스트리밍하는 소프트웨어 및 서비스를 구현하는 것이 목적입니다.
과제 이해를 위해 live tracking 서비스가 활용되는 예시를 말씀드릴게요.
고정된 카메라로 공을 차는 사람을 촬영한다고 가정하겠습니다. 이 장면에서 공과 공을 차는 사람을 인식하고, 트래킹한 장면을 실시간으로 스트리밍한다면, 시청자는 실시간으로 트래킹 되는 영상을 즐길 수 있습니다.
궁극적으로 시청자에게는 풍부한 콘텐츠를, 제작자에게는 풍부한 제작소스를 제공할 수 있습니다!
![](https://devocean.sk.com/editorImg/2022/11/30/9f514da724b7d8e72ff917d7bc8630af5a55dd683e6c40b6c2ae0caf71e2de4f)


소프트웨어 다이어그램은 다음과 같습니다.
제작자로부터 카메라로 촬영 중인 영상을 실시간으로 받아와서 프레임 단위로 Object detection과 SceneCropping을 진행합니다. 그 결과를 WebRTC API를 통해 실시간으로 송출하게 됩니다.
앞으로 말씀 드릴 주요 개발 항목도 Object detection, SceneCropping, WebRTC 입니다!
![](https://devocean.sk.com/editorImg/2022/11/30/0e4888cf2151211b196a2f1108fbc7ad25f5601f42c998db85b3bfdbcd20c1d1)


저희가 구현할 tracking 관련 기술 동향에는 mediapipe solution인 autoflip과 apple의 ipad에 탑재된 center stage라는 기술이 있습니다.
![image](https://devocean.sk.com/news/Live_Tracking_4.gif)
<span style="font-family:Apple Color Emoji,Segoe UI Emoji,NotoColorEmoji,Noto Color Emoji,Segoe UI Symbol,Android Emoji,EmojiSymbols;line-height:1em;white-space:nowrap;font-size:1em" aria-label="✔️" role="image">✔️ </span>**Autoflip**은 촬영된 비디오를 입력으로 받아 detection 과 crop 및 tracking을 진행합니다. 저희의 연구 과제인 라이브 트래킹은 카메라 입력 영상을 실시간 처리를 한다는 점에서 큰 차이가 있습니다.
![image](https://devocean.sk.com/news/Live_Tracking_5.gif)
<span style="font-family:Apple Color Emoji,Segoe UI Emoji,NotoColorEmoji,Noto Color Emoji,Segoe UI Symbol,Android Emoji,EmojiSymbols;line-height:1em;white-space:nowrap;font-size:1em" aria-label="✔️" role="image">✔️ </span>**Center Stage**는 ipad를 이용한 화상통화 중 사용되는 기술로 실시간 처리가 가능합니다.
그러나 이 기술은 ipad에 탑재된 카메라를 하드웨어 제어를 통해 zoom in/out 트래킹을 하는 반면, 라이브 트래킹은 입수 되는 영상 처리를 통해 프레임을 처리하기 때문에 전용 카메라 하드웨어를 사용하는 center stage보다 범용적으로 사용될 수 있다는 것이 큰 장점 입니다. 또한 ML 및 영상 처리는 소프트웨어만으로도 구현 가능하다는 점도 주목할만 합니다.


최종 산출물은 다음과 같은 웹사이트 형태로 산출되며, 광각카메라를 통해 입력되는 영상에서 피사체를 detection하고 사용자가 원하는 화면 비율에 따라 crop및 트래킹하여 실시간으로 스트리밍 하는 서비스입니다.
![](https://devocean.sk.com/editorImg/2022/11/30/cf8ec0a95d5decd8702099dbacad50291486457039ff0c267089fe0f61defce1)

<br>
## **Object Detection**

다음은 저희가 detection을 구현하기 위해 사용한 모델 및 개발 이슈에 관해 알려드릴게요.
저희는 detection의 정확도를 높이기 위해 face detection과 object detection을 구현하였습니다.
![](https://devocean.sk.com/editorImg/2022/11/30/d5d907beb762790db303d3477c20f45c82c4e1549705c93aea95b4ac3dc367d6)

먼저 face detection은 mediapipe의 solution을 활용하였습니다. blazeface기반의 얼굴검출 프레임워크로 보이는 사진처럼 총 6개의 랜드마크로 얼굴을 감지합니다.



object detection은 두개의 모델을 사용해보았습니다. 측정지표는 mAP와 fps를 사용했습니다.
앞으로 말씀 드릴 개발 상황 및 이슈는 ***Apple M1 CPU 8 cores, mem 16GB LPDDR4*** 를 개발 환경으로 사용한 점을 참고해주세요!
![](https://devocean.sk.com/editorImg/2022/11/30/901cec12514ddbc16c577f381e6b7242bcc856d6a17961250fa4196a3501bcd7)
개발 초기에 fps와 bounding box의 크게 두가지 이슈가 존재하였습니다.

<span style="font-family:Apple Color Emoji,Segoe UI Emoji,NotoColorEmoji,Noto Color Emoji,Segoe UI Symbol,Android Emoji,EmojiSymbols;line-height:1em;white-space:nowrap;font-size:1em" aria-label="✔️" role="image">✔️ </span>fps이슈에 대해 먼저 알려드릴게요. 실시간 처리를 구현하려면 fps 30이상의 성능이 필요한데, 처음 MobileNet v2 기반 ssd 모델을 돌렸을 때 fps가 2\~3프레임 정도 밖에 나오지 않을 정도로 낮았습니다.
알고리즘 처리를 최대한 단순화해서 fps를 약 **1**6 프레임까지 올리는데에 성공하였으나, 하지만 여전히 실시간 처리를 구현하기에는 부족하였습니다. yolov3-tiny모델을 사용했을 때는 fps가 23-24로 역시 실시간처리로 구현하기에 부족하였습니다.

<span style="font-family:Apple Color Emoji,Segoe UI Emoji,NotoColorEmoji,Noto Color Emoji,Segoe UI Symbol,Android Emoji,EmojiSymbols;line-height:1em;white-space:nowrap;font-size:1em" aria-label="✔️" role="image">✔️ </span>두번째로 bounding box가 잘 생성이 되지 않는 이슈가 존재하였습니다.
mediapipe autoflip에 기재된 anchor를 참고하여 box 좌표 값들을 decoding하였지만 bounding box가 피사체를 담아내지 못하였습니다.

![](https://devocean.sk.com/editorImg/2022/11/30/60fd43da698f1826fe83921777d20b5f6e214f51f33a7b530d00c7328f230967)

<br>
앞서 말씀 드렸던 이슈들은 mobilenet v1기반의 ssd모델로 바꾸었더니 해결되었습니다.
모바일넷v1과 v2는 성능 면에서는 차이가 거의 없으나, 속도는 v1이 훨씬 빨랐습니다. 더하여 tensorflow에서 제공하는 함수로 사용하여 속도를 높일 수 있었습니다.

<br>
## **Scene Cropping**

다음으로는 **Scene Cropping** 개발 상황에 대해 알려드릴게요!
우선 두 모델에서 얻은 디텍션 정보들을 종합하고 mAP score에 따라 정렬하는 방식으로 정보를 전처리하였습니다.
![](https://devocean.sk.com/editorImg/2022/11/30/3e90a0a48db0b7bd49ad9f4edbe87893a6837dd2ee495913e332578414f96089)
또한 처리할 좌표를 줄이고자 한 사람 안에서 잡히는 face 좌표와 object 좌표 중 mAP score가 높은 정보만 남기는 방식을 채택했습니다.



Scene Cropping을 구현하기 위해서는 detection 정보들을 이용해서 crop할 프레임의 중심 좌표를 정해야 합니다.
✔️ 첫 번째로 디텍션 정보가 없을 때는 원본 프레임의 중심을 기준으로 crop하였습니다. 해당 경우에서는 프레임을 자르지 않고 원본 프레임을 그대로 보여주는 것도 고려하고 있습니다.
✔️ 두 번째로 디텍션 정보가 있을 때입니다. 가장 mAP score가 높은 정보 기준으로 순차적으로 탐색하면서 설정한 경계 범위 안에 다른 디텍션의 중심 좌표가 들어올 수 있을 때, 해당 정보를 추가하는 방식으로 구현하고 있습니다.
![image](https://devocean.sk.com/news/Live_Tracking_11.gif)



<br>
Scene Cropping시에는, 위 사진과 같이 프레임이 흔들리는 경우가 발생합니다. 이러한 문제가 발생하는 이유는 피사체의 위치가 크게 바뀌지 않더라도 모델이 주는 좌표 값은 바뀌기 때문입니다.
따라서 프레임을 잡아주기 위해 프레임 보간법을 고안하였습니다. 보간은 두 지점의 값 사이에 위치한 값을 추정하는 것을 의미합니다.
crop할 두 프레임 사이에 중심 좌표 차이가 존재할 때, 그대로 전송하면 프레임이 흔들리는 경우가 발생합니다. 따라서 두 중점 좌표를 기준으로 보간한 값들로 crop한 프레임들을 송출하여 영상이 자연스럽게 보이도록 할 때 프레임 보간을 사용합니다.



기존의 프레임 보간법을 실시간으로 사용하는 데에는 다음과 같은 문제점들이 있습니다.
✔️ interpolation은 두 프레임을 기준으로 이루어져야 하는데 실시간 스트리밍에서는 다음에 오는 프레임을 알 수 없습니다.
✔️ 실시간에서는 또한 timestamp를 고려할 수 없으며 프레임과 프레임 사이에 다른 프레임들을 채우는 것은 불가능합니다.
![](https://devocean.sk.com/editorImg/2022/11/30/b12d03863001ea9bb7e027fbf82c33ecec805a2be7a5f15340e1f3ac34effd62)

따라서 다음과 같

은 방법으로 앞의 문제들을 해결하였습니다.
우선 이전 프레임의 중심 좌표를 저장하여 현재 프레임과 이전 프레임의 좌표를 기준으로 보간을 진행하고 있습니다.
시간 정보에 대한 문제는 보간할 프레임의 개수를 미리 정하는 방식으로 해결하였습니다. 보간법은 euclidean norm(유클리디엄 놈)을 사용하고 있습니다.



프레임 보간 후에 테스트를 해보았을 때, 이전 영상과 비교했을 때 프레임이 흔들리는 현상이 많이 개선된 것을 확인할 수 있었습니다!

<br>
## **WebRTC**

다음으로 세번째 개발 항목인 **WebRTC를 이용한 초저지연 스트리밍**에 대해 설명드리겠습니다.
실시간 스트리밍 기술 중 WebRTC를 저희 과제에 채택한 가장 큰 이유는, 바로 1초 이하의 Latency 때문입니다.
뿐만 아니라 WebRTC는 다양한 오픈소스 라이브러리를 공개하고 있습니다. 시청자들이 촬영 장면을 몰입하며 시청하기 위해서는, 지연이 거의 없는 WebRTC가 가장 적합한 실시간 스트리밍 포맷입니다.
![](https://devocean.sk.com/editorImg/2022/11/30/b9eb8f1bc71e63737c75afdae9a52a23b8e02052c309684b159e795624714c93)

<br>
<br>
현재 WebRTC Signaling 서버는 아래 사진의 오른쪽 상단처럼 Mesh 방식으로 구축되어 있으나, 다수의 시청자와 미디어 품질을 위해 아래처럼 SFU 구조의 서버를 개발 중입니다.
![](https://devocean.sk.com/editorImg/2022/11/30/28ea1de3876cdbede895ea318b308ad20e46e5836d364fe9b6ce7cd17b440a8e)


WebRTC 스트리밍을 개발하면서 발생한 이슈는 두 가지가 있었습니다.


<span style="font-family:Apple Color Emoji,Segoe UI Emoji,NotoColorEmoji,Noto Color Emoji,Segoe UI Symbol,Android Emoji,EmojiSymbols;line-height:1em;white-space:nowrap;font-size:1em" aria-label="✔️" role="image">✔️</span> 먼저 브라우저별 호환성 문제인데요. Chrome과 Safari에서는 스트리밍이 잘 되지만, Edge 브라우저에서는 영상이 재생되지 않았습니다.
이 이슈는 사용 중인 WebRTC 라이브러리의 기능별 호환성을 검토하여 해결할 예정입니다.
<span role="image" aria-label="✔️" style="font-family:Apple Color Emoji,Segoe UI Emoji,NotoColorEmoji,Noto Color Emoji,Segoe UI Symbol,Android Emoji,EmojiSymbols;line-height:1em;white-space:nowrap;font-size:1em">✔️</span> 둘째로 Audio의 하울링 이슈가 있었으나, 이는 WebRTC API에 내장된 Echo Cancellation이라는 기능으로 해결할 계획입니다.


나아가 스트리밍 관련 앞으로의 세부 계획을 말씀드리겠습니다.
먼저 초기 로딩시간을 줄이기 위해 트랙 선택을 최적화하고, 중복 로딩 방지 방안을 연구할 예정입니다.
또한 영상 처리에 따른 Latency를 개선하기 위하여, 스트리밍 지표의 성능을 조사한 다음, 주요 Latency 영향 요인을 분석할 예정입니다.
주요 스트리밍 지표에는 7가지(Packet Loss, NAK Count, Keyframe Interval, RTT / Delay, Bit Rate, Jitter Buffer Delay)가 있으며, <span data-reactroot="" class="notion-enable-hover" data-token-index="1" style="font-weight:600">WebRTC-Internal </span>이라는 Tool로 이 지표 값들을 측정하려 합니다!


이제 이 WebRTC 기술을 통해서 영상 처리된 video를 스트리밍해야 하는데, 저희는 이 스트리밍 영상을 웹 브라우저 상에서 시청하기로 구상했었습니다.
그러나 python 코드로 영상 처리된 video를, JS로 구축된 Signaling Server에 실시간으로 전송하는 과정이 쉽지 않았습니다.


모델링 부분과 이 스트리밍 서버를 연동하려는 방법이 3가지가 있었는데요.
첫번째, JS로 구축된 서버에서 python 스크립트를 로드하는 방식으로는 실시간 영상 데이터를 로드할 수 없었습니다.
다음으로 영상 처리를 JS로 작성하는 방식으로는 고도화된 영상 처리가 쉽지 않았습니다.
따라서 마지막으로 python으로 서버를 구축하고, 영상 처리 코드를 연동하는 방식을 채택했습니다.


세 번째 솔루션으로 모델 및 영상 처리 라이브러리를 웹앱에 탑재하여서,
![](https://devocean.sk.com/editorImg/2022/11/30/1debe7e567ff6d7259723cbcbd9492bc697c2dfe7a234ac1985aac753c0a1605)최종 산출물로서 라이브 트래킹 영상을 시청할 수 있는 웹앱을 만들어냈습니다.
![](https://devocean.sk.com/editorImg/2022/11/30/dd4c7c9cfca40f107992029c1f5cea3e54aeed405ad30bf18502ffd5d1b62c6b)


주요 기능으로 해상도나 비디오 코덱 등의 옵션을 설정한 후, 방에 입장하여 다음과 같이 트래킹되는 영상을 시청할 수 있습니다.
이런 식으로 피사체가 주어진 프레임에서 옆으로 이동하면, 같은 방향으로 트래킹되는 과정을 실시간으로 볼 수 있습니다!
![](https://devocean.sk.com/editorImg/2022/11/30/e77715da04af97384272c568cbb1d1c6d53778db36b4137ee8b69bcbb4bd063d)


지금까지 *Team* <span style="color: #0ac90b">금쪽이들</span>이었습니다! 😎


***
1. 위 파일들과 yolov3-tiny.weights 파일 다운
https://velog.io/@jeongm/yolov3-weight%EA%B0%80%EC%A4%91%EC%B9%98-%EB%8B%A4%EC%9A%B4

2. LiveTracking 파일 실행
