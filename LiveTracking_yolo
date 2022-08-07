#!/usr/bin/env python
# coding: utf-8

import cv2
import numpy as np
from time import time
import math
import sys 
from time import time

min_confidence = 0.4 # bounding box 임계값
t= 0

#------------------------------------------------------------------------------------------

def detectAndDisplay(frame):
    img = frame
    height, width, channels = img.shape

    blob = cv2.dnn.blobFromImage(img, 0.00392, (384, 384), (0, 0, 0), True, crop=False)

    net.setInput(blob)
    outs = net.forward(output_layers)

    # 탐지한 객체의 클래스 예측 
    class_ids = []
    confidences = []
    boxes = []

    for out in outs:
        for detection in out:
            scores = detection[5:]
            class_id = np.argmax(scores)
            confidence = scores[class_id]
            # 원하는 class id 입력 ex) person == 1, cat ==16 / coco.names의 id에서 -1 해서 넣어주면 됨
            if class_id == 0 and confidence > min_confidence:
                # 탐지한 객체 boxing
                center_x = int(detection[0] * width)
                center_y = int(detection[1] * height)
                w = int(detection[2] * width)
                h = int(detection[3] * height)
               
                x = int(center_x - w / 2)
                y = int(center_y - h / 2)

                boxes.append([x, y, w, h])
                print(x, y, w, h)
                confidences.append(float(confidence))
                class_ids.append(class_id)

    indexes = cv2.dnn.NMSBoxes(boxes, confidences, min_confidence, 0.4)
    font = cv2.FONT_HERSHEY_DUPLEX
    
    for i in range(len(boxes)):
        if i in indexes:
            x, y, w, h = boxes[i]
            label = "{}: {:.2f}".format(classes[class_ids[i]], confidences[i]*100)
            color = colors[i] #-- 경계 상자 컬러 설정 / 단일 생상 사용시 (255,255,255)사용(B,G,R)
            cv2.rectangle(img, (x, y), (x + w, y + h), color, 2)
            cv2.putText(img, label, (x, y - 5), font, 1, color, 1)
    
    return boxes

#--------------------------------------------------------------------------------------------
# yolo 포맷 및 클래스명 불러오기
model_file = 'yolov3-tiny.weights'# 모델
config_file = 'yolov3-tiny.cfg'# 모델

net = cv2.dnn.readNet(model_file, config_file)

# 클래스(names파일)
classes = []
with open("./coco.names", "r") as f:
    classes = [line.strip() for line in f.readlines()]
    
layer_names = net.getLayerNames()
output_layers = [layer_names[i-1] for i in net.getUnconnectedOutLayers()]
print(output_layers)

colors = np.random.uniform(0, 255, size=(len(classes), 3))

# 카메라 input
cap = cv2.VideoCapture(0)

if not cap.isOpened:
    print('--(!)Error opening video capture')
    sys.exit(1)

Ghh = cap.get(cv2.CAP_PROP_FRAME_HEIGHT)
Gww = cap.get(cv2.CAP_PROP_FRAME_WIDTH)

Ghh, Gww = int(Ghh), int(Gww)

#x, y, w, h = rect
x = int(Gww*0.1)
y = int(Ghh*0.1)
w = int(Gww*0.8)
h = int(Ghh*0.8)

# 필요 변수 선언
i = 0 # frame count & 저장 리스트 비교용
tmp = 0 # 첫번째 detection 구분
notcnt = 0 # 아무것도 검출이 안되는 상황 대비, 일정 카운트 이상일 시 원본 frame 크기로 변경
case_not = 0 # 검출이 안되다가 갑자기 검출될 시 발생하는 예외 제거
j = 1 # 프레임 별 시간 계산용
time_tmp = 0 # 시간 cnt 시작

t1 = 0.0

# 프레임 간 좌표 계산을 위한 저장용 list 생성, 초기값 append
PX = []
PY = []
X_min = []
X_max = []
Y_min = []
Y_max = []
X_min.append(x)
X_max.append(x+w)
Y_min.append(y)
Y_max.append(y+h)

PX.append((X_max[i] + X_min[i])/2)
PY.append((Y_max[i] + Y_min[i])/2)


tt_i = time()
while cap.isOpened():
    tt0 = time()
    success, img = cap.read()
    if not success:
      print("Ignoring empty camera frame.")
      break       
    
    box = detectAndDisplay(img)
    cv2.imshow('autocrop', img)

    # 객체 검출될 시
    if len(box) > 0:
        x = box[0][0]
        y = box[0][1]
        w = box[0][2]
        h = box[0][3]
        notcnt = 0
        if case_not > 0:
            case_not-=1

        x_ = int((2*x-w) / 2)
        y_ = int((2*y-h) / 2)
        w_ = int(2*w)
        h_ = int(2*h)

        if x_ <= 0: x_ = 0
        if y_ <= 0: y_ = 0

        xw = x_ + w_
        yh = y_ + h_

        if xw >= Gww: 
            xw = Gww
        if yh >= Ghh: 
            yh = Ghh

        X_min.append(x)
        X_max.append(x+w)
        Y_min.append(y)
        Y_max.append(y+h)
        
        image = img[:, x+(w//2)-200:x+(w//2)+200]
    else:
        image = img[:, 440:840]

    j+=1
    
    cv2.imshow('autocrop', image)
    
    key_pressed = cv2.waitKey(1) & 0xFF
    if key_pressed == ord('q'):
        break
        

cap.release()
cv2.destroyAllWindows()
