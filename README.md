# AI를 통한 시각장애인 대중교통 접근성 향상 프로젝트
<svg role="img" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><title>OpenCV</title><path d="M11.8992.8525C8.735.8525 6.17 3.4175 6.17 6.5817c0 2.102 1.1321 3.9398 2.8198 4.9366l1.6412-2.7849c.0411-.0699.0176-.1593-.0495-.2048-.6233-.4227-1.0328-1.137-1.0328-1.947 0-1.298 1.0524-2.3504 2.3505-2.3504 1.2981 0 2.3505 1.0524 2.3505 2.3505 0 .8098-.4095 1.5242-1.0328 1.947-.0671.0454-.0907.1348-.0495.2047l1.6414 2.785c1.6878-.9969 2.8199-2.8346 2.8199-4.9367 0-3.1642-2.5653-5.7292-5.7295-5.7292zm-6.17 10.8366C2.565 11.6891 0 14.2541 0 17.4183c0 3.1642 2.565 5.7292 5.7292 5.7292 3.1798 0 5.8074-2.6995 5.7275-5.8762H8.2313c-.0847 0-.1513.0717-.1519.1564-.0082 1.266-1.0644 2.3411-2.3502 2.3411-1.2981 0-2.3505-1.0524-2.3505-2.3505 0-1.2982 1.0524-2.3505 2.3505-2.3505.34 0 .663.0724.9547.2022.0713.0318.1566.0077.1962-.0595l1.6464-2.7935c-.8273-.4636-1.7815-.7279-2.7973-.7279zm15.4424.7614l-1.6366 2.7878c-.041.07-.0172.1594.05.2048.624.4217 1.0348 1.1354 1.0363 1.9452.0022 1.298-1.0483 2.352-2.3465 2.3542-1.298.0023-2.3523-1.0482-2.3545-2.3462-.0015-.8098.4068-1.5248 1.0294-1.9486.067-.0457.0905-.1353.0492-.2051l-1.6464-2.7818c-1.6859.9998-2.8146 2.8394-2.811 4.9415.0056 3.1641 2.575 5.7248 5.7393 5.7192 3.1641-.0054 5.7246-2.575 5.7192-5.7392-.0037-2.1022-1.139-3.938-2.8284-4.9318z"/></svg>
💻 ## 시연 자료
- 버스 번호 추론
![image](https://github.com/K-Software-BootCamp/2023KEB_Murado-Ssul-Ja/assets/108107570/b38f67d5-99b2-4821-b971-102ebddc6eef)
- 원본사진 -> 흑백 -> 이진화
![image](https://github.com/K-Software-BootCamp/2023KEB_Murado-Ssul-Ja/assets/108107570/a411b59b-2423-40be-a90a-75347a14a1b6)
- 버스 번호 출력
![image](https://github.com/K-Software-BootCamp/2023KEB_Murado-Ssul-Ja/assets/108107570/5b9aab3f-cee8-42c6-ad8b-5580cace3897)


## 프로젝트 흐름도
<img width="505" alt="image" src="https://github.com/K-Software-BootCamp/2023KEB_Murado-Ssul-Ja/assets/140637787/f5a5c66a-3be8-4296-8607-1a6d311cad27">

  1. 아두이노 젯슨에 연결된 카메라를 통해 정류장으로 진입하는 영상을 촬영한다.
  2. 젯슨의 docker container에 있는 yolov5 모델을 이용하여 버스 번호를 detection한다.
  3. pyserial 라이브러리를 활요하여 젯슨에서 아두이노로 시리얼 통신을 통해 detection된 데이터를 전송한다.
  4. 아두이노에서 수신한 데이터에 맞는 버스 번호를 mp3 모듈을 통해 출력한다.
  5. 이용자는 아두이노에 있는 이어폰 단자를 이용하여 간편하게 버스 번호를 알려주는 음성 정보를 얻는다.


## 프로젝트 선정 동기 

![image](https://github.com/K-Software-BootCamp/2023KEB_Murado-Ssul-Ja/assets/140637787/dfa1cdb4-e052-4992-b6c7-198d07259e2f)

위 자료에서 알 수 있듯이, 시각 장애인이 이용하기 가장 힘든 교통수단은 버스이며 그 이유는 그들이 버스 번호를 인식하기 힘들다는 것이다. 그래서, 우리는 AI와 기술을 통해 교통약자들의 문제를 해결하자는 목표를 갖고 해당 프로젝트 주제를 선정했다.

## 사용법
1. BusNumber Detection 모델인 best.pt 파일과 BusNumberDetect.py 파일 다운로드
```
git clone git@github.com:K-Software-BootCamp/2023KEB_Murado-Ssul-Ja.git
```

2. Yolov5 설치
```
git clone https://github.com/ultralytics/yolov5.git
cd yolov5
pip install -r requirements.txt
```

3. BusNumberDetect.py 파일과 best.pt 파일을 경로에 맞게 이동
```
mv ~/2023KEB_Murado-Ssul-Ja/BusNumberDetect.py /yolov5
mv ~/2023KEB_Murado-Ssul-Ja/best.pt /yolov5
```

4. 버스가 나오는 이미지나 유튜브 링크를 source로 사용하여 BusNumberDetect.py 실행
```
!python3 BusNumberDetect.py --werights best.pt --source <img, video, webcam, youtube link> 
```


### Acknowledgement
```
"본 연구는 과학기술정보통신부 및 정보통신기획평가원의 SW전문인재양성사업의 연구결과로 수행되었음"(2022-0-01127)
```
