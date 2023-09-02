# Live_Tracking_yolo


<span style="mso-fareast-font-family:맑은 고딕;mso-fareast-theme-font:
minor-latin">안녕하세요</span><span lang="EN-US">! SKT AI Fellowship 5</span>번 연구과제 <span lang="EN-US"><</span>라이브 트래킹<span lang="EN-US">></span>을 연구하고 있는 <span lang="EN-US">Team</span>금쪽이들의 김지은 입니다<span lang="EN-US">.</span>


지금부터 제가 <span lang="EN-US">AIF</span>과제를 위해서 공부해왔던 것들에 대해 소개해보려고 해요<span lang="EN-US">! 😀</span>


<span style="mso-fareast-font-family:맑은 고딕;
mso-fareast-theme-font:minor-latin" lang="EN-US"> </span>
<span style="mso-fareast-font-family:맑은 고딕;mso-fareast-theme-font:
minor-latin">처음 제 글을 읽으시는 분들을 위해, 간단하게 과제 소개를 해볼게요.</span>
<span style="mso-fareast-font-family:맑은 고딕;mso-fareast-theme-font:
minor-latin">라이브 트래킹이란 실시간으로 촬영 중인 영상 내에서 움직이는 피사체를 인식해 자동으로 트래킹해주는 기술이에요</span><span lang="EN-US">.</span>
![](https://devocean.sk.com/editorImg/2022/11/11/a9c479b45253dcd845847102724ef3f5c688e17cf57e501b7d3eb212e8f821b7)


***


기술의 배경 및 필요성에 대해서도 궁금하시죠<span lang="EN-US">?</span>
현재 비디오 스트리밍 분야에서 유튜브<span lang="EN-US">, </span>트위치 등의 라이브 스트리밍 플랫폼이 활발하게 이용되고 있어요<span lang="EN-US">.</span>
이러한 환경 속에 직접 콘텐츠를 제작<span lang="EN-US">, </span>스트리밍하려는 개인 콘텐츠 창작자들이 다수 등장하고 있으며<span lang="EN-US">, </span>라이브 콘텐츠 제작에 관심이 커지고 있는 트렌드입니다<span lang="EN-US">.</span>
이런 트렌드 속 라이브 트래킹 기술은 창작자 입장에서도<span lang="EN-US">, </span>시청자 입장에서도 편리하고 필요한 기술이라고 할 수 있어요<span lang="EN-US">!</span>
기술 이해를 조금 더 쉽게 도와드리자면<span lang="EN-US">, mediapipe</span>의 <span lang="EN-US">Autoflip</span>과 아이패드의 <span lang="EN-US">center stage </span>기술을 비슷한 기술로 꼽을 수 있어요.


최종 산출물은 다음과 같은 웹사이트 형태로 산출될 예정이에요.
![](https://devocean.sk.com/editorImg/2022/11/11/af1ee8908f5bf07f039eaf75405db9a8456c35740c8a879ed4ab42d6c64e5802)
광각카메라를 통해 입력되는 영상에서 피사체를 detection하고 사용자가 원하는 화면 비율에 따라 crop및 트래킹하여 실시간으로 스트리밍 하는 서비스가 될 예정입니다!

***

<br>
<span style="mso-fareast-font-family:맑은 고딕;
mso-fareast-theme-font:minor-latin" lang="EN-US">그럼 이제 제가 공부한 분야에 대해 소개해볼게요!</span>
<span style="mso-fareast-font-family:맑은 고딕;mso-fareast-theme-font:
minor-latin">개발 분야는 크게 모델링과 </span><span lang="EN-US">WebRTC </span>부분으로 나뉘는데요<span lang="EN-US">. </span>저는 모델링 개발을 담당하였습니다<span lang="EN-US">.</span>
<span style="mso-fareast-font-family:맑은 고딕;mso-fareast-theme-font:
minor-latin">모델 개발 초기 진행 상황부터 현재 개발 상황까지의 과정에 대해 살펴볼게요</span><span lang="EN-US">!</span>
<span style="mso-fareast-font-family:맑은 고딕;mso-fareast-theme-font:
minor-latin">저희 팀은 </span><span lang="EN-US">2-3</span>주의 <span lang="EN-US">sprint</span>를 설정하고 그에 따라서 정한 <span lang="EN-US">task</span>들을 해결하며 개발 과정을 설정하였습니다<span lang="EN-US">.</span>


각 Sprint 별로 과제 연구가 어떻게 이루어졌는지 궁금하시죠?
<span style="mso-fareast-font-family:맑은 고딕;
mso-fareast-theme-font:minor-latin" lang="EN-US">Sprint1</span><span style="mso-fareast-font-family:
맑은 고딕;mso-fareast-theme-font:minor-latin">에서는 환경 세팅 및 자료 조사를 진행하였어요</span><span lang="EN-US">. AIF </span>과제를 진행하며 <span lang="EN-US">Mac</span>을 처음 사용해보았기 때문에<span lang="EN-US">, </span>익숙해지는 과정을 거쳤답니다<span lang="EN-US">.</span>
제일 먼저 앞서 말씀드린 <span lang="EN-US">mediapipe</span>의 <span lang="EN-US">Autoflip </span>코드를 사용해보았어요<span lang="EN-US">.</span><span style="mso-fareast-font-family:맑은 고딕;
mso-fareast-theme-font:minor-latin" lang="EN-US"> </span>
<span style="mso-fareast-font-family:맑은 고딕;
mso-fareast-theme-font:minor-latin" lang="EN-US"> ![](https://devocean.sk.com/editorImg/2022/11/11/c21cae98a1dba707395108f6dedbe36ab481f9d6663738a1670567296a881f77)</span>

<br>
**Autoflip 코드 실행**
김연아 선수의 무대 영상을 Autoflip을 이용하여 트래킹한 결과 입니다.
물론 Autoflip을 사용해보는 것도 쉽지는 않았어요. 하지만 많은 에러들을 해결하고 저희가 구현하고자하는 라이브 트래킹과 비슷한 기술을 경험해보았습니다!


원래 계획은 mediapipe의 이 Autofilp을 사용하여 실시간 입력을 통해서 라이브 트래킹을 구현하려고 하였어요.
하지만 직접 사용해보니, Autoflip의 로직 자체가 많이 복잡하고, 실시간 Input을 사용하는 저희 팀의 과제에 사용하는 것은 불가능하였습니다.
그래서 객체를 인식하는 기술인 Object Detection과 Tracking알고리즘을 통해서 직접 개발하기로 결정하였습니다.
앞으로 말씀 드릴 개발 내용은 Autoflip의 로직을 많이 참고하여서 연구하였습니다!


저는 Object Detection을 구현한 모델 중에서도 가장 널리 알려지고, 익숙한 YOLO모델을 사용해보았어요.
Yolov3 tiny model로 object detection 후 박스 범위에 따라 자동 크롭을 구현하였습니다.
<span style="mso-no-proof:yes">![]() ![](https://devocean.sk.com/editorImg/2022/11/11/b0514de154f8d7924a8fe322cd1f34502f6d027736b9e8531e3e50adfeeeae2b)![]()</span>

<br>
객체를 중심을 잡히는 박스의 <span lang="EN-US">x,y,w,h</span>을 기준으로 임의로 어느정도 범위를 정해서 크롭 되도록 하였습니다<span lang="EN-US">.</span>
<span style="mso-fareast-font-family:맑은 고딕;mso-fareast-theme-font:
minor-latin">매 </span><span lang="EN-US">Sprint </span>중간과 사이사이 팀원들과 주기적으로 회의 시간을 가졌는데요<span lang="EN-US">. </span>팀원들과 회의 후<span lang="EN-US">, </span>박스 기준으로 크롭할 필요성을 없다고 판단되었습니다<span lang="EN-US">.</span>
<span lang="EN-US">Detection</span>된 객체의 중심 좌표값만 알면<span lang="EN-US">, </span>그것을 중심으로 <span lang="EN-US">16:9, 3:4 </span>와 같이 일정 비율로 <span lang="EN-US">crop</span>할 수 있다는 거죠<span lang="EN-US">!</span>
![](https://devocean.sk.com/editorImg/2022/11/11/d55aaa5014ac8f438f75486744d4b508ceaf9eb47f3a84500072dfd477ca97dd)
<span style="mso-fareast-font-family:맑은 고딕;mso-fareast-theme-font:
minor-latin">회의 후</span><span lang="EN-US">, </span>수정한 비율로 <span lang="EN-US">crop</span>해보았습니다<span lang="EN-US">. Yolo tiny </span>모델을 사용하였을 때<span lang="EN-US">, </span>몇가지 문제점이 존재했습니다<span lang="EN-US">. Real-time</span>은 <span lang="EN-US">fps</span>가 <span lang="EN-US">30</span>이상으로 나오면 안정적으로 구현 가능합니다<span lang="EN-US">.</span>
하지만 <span lang="EN-US">yolo-tiny</span>를 사용하였을 때<span lang="EN-US">, fps</span>가<span lang="EN-US"> 23-24 </span>정도로 나왔습니다<span lang="EN-US">. </span>또한 <span lang="EN-US">crop</span>기능을 넣으면서<span lang="EN-US"> detection</span>이 느려지고 부드럽게 <span lang="EN-US">crop</span>이 이어지지 않았습니다<span lang="EN-US">.</span>
또한 아무래도 속도를 위해서 <span lang="EN-US">tiny</span>모델을 사용하다보니<span lang="EN-US">, Detection</span>의 정확도도 떨어지는 단점이 존재하였습니다<span lang="EN-US">.</span>
<span style="mso-fareast-font-family:맑은 고딕;
mso-fareast-theme-font:minor-latin" lang="EN-US"> </span>
<span style="mso-fareast-font-family:맑은 고딕;mso-fareast-theme-font:
minor-latin">팀원 중 같이 모델링 개발 부분을 담당한 민솔 팀원이 </span><span lang="EN-US">Mobilenet v1 SSD lite</span>라는 <span lang="EN-US">detection </span>모델로 테스트를 진행중이었습니다<span lang="EN-US">.</span>
<span lang="EN-US">SSD </span>모델이 <span lang="EN-US">fps </span>성능이 더 좋았고<span lang="EN-US">, tracking</span>도 더 자연스럽게 진행이 되었기 때문에<span lang="EN-US">, Object Detection </span>모델을 <span lang="EN-US">Mobilenet v1 SSD lite</span>로 사용하기로 결정하였습니다<span lang="EN-US">.</span>
<span style="mso-fareast-font-family:맑은 고딕;
mso-fareast-theme-font:minor-latin" lang="EN-US"> </span>
<span style="mso-fareast-font-family:맑은 고딕;mso-fareast-theme-font:
minor-latin">또한 </span><span lang="EN-US">mediapipe</span>의 <span lang="EN-US">blazeface</span>를 <span lang="EN-US">Object Detection</span>과 함께 사용하기로 하였습니다<span lang="EN-US">.</span>
![](https://devocean.sk.com/editorImg/2022/11/11/cc389d380b1bb34f9cb402cce3aaf65026e4720da4f5714e0cbcade4c89758fa)
<span style="mso-no-proof:yes">![]()</span>mediapipe - blazepose


객체를 인식하는 것만 하는 것이 아니라<span lang="EN-US">, </span>얼굴 좌표 값을 통해 얼굴을 인식한다면 조금 더 높은 정확도로 객체를 트래킹할 수 있기 때문이에요<span lang="EN-US">!</span>
<span lang="EN-US">Blazeface</span>를 통해 인식한 얼굴과 <span lang="EN-US">Object Detection</span>모델을 통해 인식한 객체 중<span lang="EN-US">, </span>더 높은 정확도를 보이는 <span lang="EN-US">Box</span>를 기준으로 <span lang="EN-US">Tracking</span>을 진행하도록 알고리즘을 작성하였습니다<span lang="EN-US">.</span>
<span style="mso-fareast-font-family:맑은 고딕;
mso-fareast-theme-font:minor-latin" lang="EN-US"> </span>
<span style="mso-fareast-font-family:맑은 고딕;mso-fareast-theme-font:
minor-latin">하지만 여전히 </span><span lang="EN-US">tracking</span>이 보기에 부드러울 정도로 진행되지 않는다는 단점이 존재하였습니다<span lang="EN-US">.</span>
<span style="mso-fareast-font-family:맑은 고딕;
mso-fareast-theme-font:minor-latin" lang="EN-US">Sprint3</span><span style="mso-fareast-font-family:
맑은 고딕;mso-fareast-theme-font:minor-latin">가 끝나고 멘토님과 진행한 미팅에서 매 프레임 마다 </span><span lang="EN-US">detection</span>을 진행하기 때문에 요구되는 연산이 많으니<span lang="EN-US">, detection</span>을 듬성듬성 수행해서 연산량을 줄이라는 피드백을 받았습니다<span lang="EN-US">.</span>
<span style="mso-fareast-font-family:맑은 고딕;mso-fareast-theme-font:
minor-latin">더하여</span><span lang="EN-US"> Tracking </span>알고리즘도 더 좋은 성능을 위한 방법을 고민해보았습니다<span lang="EN-US">.</span>
<span style="mso-fareast-font-family:맑은 고딕;
mso-fareast-theme-font:minor-latin" lang="EN-US"> </span>
<span lang="EN-US">Object Tracking Methods </span>자료 조사를 진행한 결과<span lang="EN-US">, SORT(</span><span class="notion-enable-hover">Simple Online Realtime Tracker)에 대해 알게되었습니다</span><span lang="EN-US">. SORT</span>는 다중 객체 탐지 알고리즘<span lang="EN-US"> MOT(Multi Object Tracking) </span>입니다<span lang="EN-US">.</span>
![](https://devocean.sk.com/editorImg/2022/11/11/9fa4264f1bc03cca6f72d616b73b8245057a76bd6ba2e74372051a3cf3af6218)
탐지된 객체의 경계상자를 이용하여 객체의 속도를 [<span lang="EN-US">칼만 필터(Kalman Filter)</span>]()로 추정하여 다음 프레임에서 객체의 위치를 예측하는 방식으로 사용됩니다<span lang="EN-US">.</span>
Kalman filter는 이전 프레임에 등장한 개체를 이용하여 다음 프레임의 개체의 위치를 예측하고 측정합니다.
Detection 중 발생되는 Noise를 처리하는데 도움을 준다는 특징이 있습니다.
영상에서의 Tracking은 선형성(물체가 순간적으로 사라지거나 나타나지 않음)을 나타내기 때문에 영상 Tracking에서 적합하다고 할 수 있습니다.
예를 들어<span lang="EN-US">, </span>**<span class="notion-enable-hover">N</span>**번째 프레임에서 탐지된 경계상자<span lang="EN-US"> </span>**<span class="notion-enable-hover">F</span>**는 칼만 필터로<span lang="EN-US"> </span>**<span class="notion-enable-hover">N+1</span>**번째 프레임에서의<span lang="EN-US"> </span>**<span class="notion-enable-hover">F\*</span>**를 추정하게 됩니다.
여기서<span lang="EN-US"> </span>**<span class="notion-enable-hover">N+1</span>**번째 프레임에서 새롭게 탐지된 객체 정보 **<span lang="EN-US">F'</span>**와 예측된<span lang="EN-US"> </span>**<span class="notion-enable-hover">F\*</span>**의 유사도를 [<span style="color:blue">IOU</span><span lang="EN-US">의 거리값 </span>]()그리고<span lang="EN-US"> </span>[<span lang="EN-US">헝가리안 알고리즘 </span>]()등을 통해 정렬하고 매칭하여<span lang="EN-US"> </span>**<span class="notion-enable-hover">N</span>**번째에서 탐지된 객체의 정보를<span lang="EN-US"> </span>**<span class="notion-enable-hover">N+1</span>**에서 이어나갈<span lang="EN-US">  </span>수 있게 합니다<span lang="EN-US">.</span>
이 칼만필터를 통해서 빠른 속도와 실시간 가능성을 확보할 수 있게 됩니다<span lang="EN-US">!</span>


여기서 IoU란 Intersection over Union로 Object Detection 분야에서 예측 Bounding Box와 Ground Truth가 일치하는 정도를 0과 1 사이의 값으로 나타낸 값을 말해요.
![](https://devocean.sk.com/editorImg/2022/11/11/8b82b36293ea81ad37638db5d45fab9e2bb9ec9abf7657902cd9e5b92cee8d56)
<span data-reactroot="" class="notion-enable-hover" data-token-index="0" style="font-weight:600">Object Detection에서 단순히 box의 좌표 차이를 통해 loss를 구하는 것보다 IoU를 loss에 활용하는 것이 regression loss에 더 적합해요.</span>


**헝가리안 알고리즘(Hungarian matching algorithm**\) 은 O\(\|V^3\|\)의 시간복잡도로 좀 더 효율적이고 빠르게 해결하는 알고리즘이에요\.
가중치가 있는 이분 그래프(weighted bitarted graph)에서 maximum weight matching을 찾기 위한 알고리즘이죠.
헝가리안 알고리즘에 적용되는 핵심 아이디어는 바로 “Cost matrix에서 row, column 방향으로 값을 빼거나 더한 후 최적의 연결(optimal matching)을 찾는 것은 Original Cost matrix에서 최적의 연결을 찾은 결과와 동일하다” 이에요.
즉, 복잡한 숫자로 이루어진 인접 행렬을 쉽게 변형해서 최적의 선택이 무엇인지 알기 쉽게 만든 후, 선택하자는 것이에요.


<span lang="EN-US">Deep SORT</span>는 <span lang="EN-US">sort</span>를 확장한 개념인데요. <span lang="EN-US">Sort</span>는<span lang="EN-US"> Kalman filter</span>가 뛰어나긴 하지만<span lang="EN-US">, 그 효율성에도 불구하고 </span>실제 상황에서 발생하는<span lang="EN-US"> Occulusion</span>이나<span lang="EN-US"> ID switching </span>에는 불안정하다는 한계점이 있기 때문이에요<span lang="EN-US">.</span>
![](https://devocean.sk.com/editorImg/2022/11/11/f4514409df16b8088e4af9969ac1d14e7977814faa738e9e244f502c63cee800)
<span style="color:#595959;
mso-themecolor:text1;mso-themetint:166">다른 사람들에 의해 혼자 걷고 있는 남성의</span><span lang="EN-US"> BBox</span>가 사라진 상황<span lang="EN-US">(Tracking X)</span>


<span lang="EN-US">\* Occulusion</span>은 위와 같이 개체가 어떤 상황에 의해 가려지는 현상을 말합니다<span lang="EN-US">.</span>
![](https://devocean.sk.com/editorImg/2022/11/11/72c88d82bd4633d8c10da9c1a102e37ba1131ae2cf7ad851cfba67a289b8cf84)
<span style="color: rgb(0, 0, 0); font-family: Noto Sans Light;">\* ID Switching은 MOT의 특징 중 다양한 개체가 움직일 때, ID의 추적이 변경될 수 있다는 것이에요</span>
<span style="font-family: Noto Sans Light;">예를 들어 위와 같이 축구 경기를 위에서 관찰하고 있을 때, 선수들의 ID를 추적하는 상황이 제대로 이뤄지지 않는다는 점이 있습니다.</span>
<span style="mso-no-proof:yes">![]()![](https://devocean.sk.com/editorImg/2022/11/11/5a6699343cc37effe3491af23fb311c7d83aa5d94b27824680c0f00cb5a25ee5)</span>


<span style="mso-bidi-font-size:10.0pt;
mso-fareast-font-family:맑은 고딕;mso-fareast-theme-font:minor-latin;mso-bidi-font-family:
굴림;mso-font-kerning:0pt" lang="EN-US">DeepSORT</span><span style="mso-bidi-font-size:10.0pt;
mso-fareast-font-family:맑은 고딕;mso-fareast-theme-font:minor-latin;mso-bidi-font-family:
굴림;mso-font-kerning:0pt">의 가장 큰 특징으로는</span><span lang="EN-US">Deep Appearance Descriptor </span>으로<span lang="EN-US"> Re-identification(ReID) </span>모델을 적용하여<span lang="EN-US"> ID Switching </span>문제를 해결<span lang="EN-US"> & Matching Cascade </span>로직으로 더 정확한 추적을 가능하게 해요<span lang="EN-US">.</span>
장점은 매우 빠른 추적으로<span lang="EN-US"> real-time </span>가능하고 높은 정확도를 가져<span lang="EN-US"> sort</span>에 비해<span lang="EN-US"> ID swithing이 </span>감소한다는 점이에요<span lang="EN-US">.</span>
![](https://devocean.sk.com/editorImg/2022/11/11/9f06af72a23f407d33f0cd4d19a8b86dbbdcfa1707bc3464d2970c4977c8cf83)
Deep Sort와 Sort의 성능을 분석한 논문 자료입니다.


위와 같이 조사한 <span lang="EN-US">SORT </span>알고리즘을 사용해서 <span lang="EN-US">Tracking </span>성능을 개선해보기로 하였습니다<span lang="EN-US">!</span>
<span lang="EN-US">SORT</span>를 사용하였을 때<span lang="EN-US">, Tracking</span>이 끊기면서 실행이 되는 문제점이 발생해서 <span lang="EN-US">Deep SORT</span>로 시도를 해보았습니다<span lang="EN-US">.</span>
<span class="notion-enable-hover">Deep SORT</span>는 기존<span lang="EN-US"> SORT</span>와 차이점이 있다면 <span lang="EN-US">matching cascade</span>를 진행한다는 점이에요<span lang="EN-US">.</span>
<span lang="EN-US">Matching cascadefks track</span>과 <span lang="EN-US">detection</span>과의 정보를 유사도가 큰 순서대로 <span lang="EN-US">matching</span>하는 것이에요<span lang="EN-US">.</span>
<span lang="EN-US">SORT</span>에서는 이부분이 구현되어있지 않았습니다<span lang="EN-US">.</span>
또<span lang="EN-US"> sort</span>랑 다르게 이미지를 <span lang="EN-US">feature extracting</span>한다는 점이 큰 차이였습니다<span lang="EN-US">.</span>
하지만 <span lang="EN-US">Deep SORT</span>를 사용하였을 때도<span lang="EN-US">, Tracking</span>이 잘되지 않는 문제가 발생하였습니다<span lang="EN-US">.</span>
결국 최종적으로 <span lang="EN-US">FastMOT</span>의 로직을 따와서 해결하여 현재 모델을 완성하였습니다<span lang="EN-US">!</span>


멘토님께서 연구를 위해서 <span lang="EN-US">GPU</span>서버를 사용할 수 있게해주셔서<span lang="EN-US">, Object Detection </span>모델 테스트용으로 사용해보았습니다<span lang="EN-US">.</span>
<span lang="EN-US">Real-time</span>을 구현할 수 있다고 널리 알려진 <span lang="EN-US">YOLOv4</span>와 <span lang="EN-US">YOLOv7</span>을 테스트 해보기로 하였습니다<span lang="EN-US">.</span>
<span lang="EN-US">YOLOv4</span>는 <span lang="EN-US">make </span>단계에서 에러가 계속해서 발생하였습니다<span lang="EN-US">.</span>
그래서 <span lang="EN-US">YOLOv4</span>를 테스트 해보는 데는 실패하였습니다<span lang="EN-US">.</span>
<span lang="EN-US">GPU</span>를 <span lang="EN-US">ssh</span>로 연결해서 사용해본 적은 처음이라<span lang="EN-US">, </span>많이 헤매고 시간이 들었습니다<span lang="EN-US">.</span>
특히 <span lang="EN-US">cuda</span>와 <span lang="EN-US">pytorch </span>버전 호환 문제가 계속 발생하였습니다<span lang="EN-US">. YOLOv7</span>은 <span lang="EN-US">YOLOv4</span>보다는 실행시키는 것이 간단해서 실행시키는 데는 성공하였습니다<span lang="EN-US">.</span>


모델 테스트에 있어서 몇가지 한계점이 존재하였습니다<span lang="EN-US">.</span>
먼저 테스트의 정량적 기준 설정의 어려움과 영상의 실시간 입력을 받아오는 저희 팀의 코드를 <span lang="EN-US">GPU</span>서버를 이용해서 사용하기 어려웠습니다<span lang="EN-US">.</span>
또한 <span lang="EN-US">CPU</span>를 사용한 지금 모델과 <span lang="EN-US">web</span>과의 연결도 안정적인 상황이 아니기 때문에<span lang="EN-US">, GPU</span>를 사용한다고 해도 <span lang="EN-US">web</span>과 안정적으로 연결이 될 지 확신이 서지 않았습니다<span lang="EN-US">.</span>
현재는 CPU를 이용해서 연구를 진행하기로 결정하였습니다.


현재는 특허 관련한 <span lang="EN-US">Sprint6 </span>단계로<span lang="EN-US">, </span>특허 출원 방법에 대한 조사와 특허 아이디어 구현을 목표로 연구 단계가 진행중입니다<span lang="EN-US">.</span>


그럼 앞으로도 Team 금쪽이들의 연구 지켜봐주세요!
감사합니다.

***

**[Reference]**
\- SORT와 DeepSORT의 혼합을 이용한 실시간 다중객체 추적 : [http://ki-it.com/xml/30742/30742.pdf](http://ki-it.com/xml/30742/30742.pdf)
\- Deep Sort paper : [https://arxiv.org/pdf/1703.07402.pdf](https://arxiv.org/pdf/1703.07402.pdf)
\- Sort paper : [https://arxiv.org/pdf/1602.00763.pdf](https://arxiv.org/pdf/1602.00763.pdf)


***
1. 위 파일들과 yolov3-tiny.weights 파일 다운
https://velog.io/@jeongm/yolov3-weight%EA%B0%80%EC%A4%91%EC%B9%98-%EB%8B%A4%EC%9A%B4

2. LiveTracking 파일 실행
