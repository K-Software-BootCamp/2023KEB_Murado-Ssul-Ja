# AI를 통한 시각장애인 대중교통 접근성 향상 프로젝트

### 시연 자료: 
![image](https://github.com/K-Software-BootCamp/2023KEB_Murado-Ssul-Ja/assets/108107570/bb25f83b-5842-4663-bee1-76c31e370f03)

### 프로젝트 흐름도:
<img width="505" alt="image" src="https://github.com/K-Software-BootCamp/2023KEB_Murado-Ssul-Ja/assets/140637787/f5a5c66a-3be8-4296-8607-1a6d311cad27">

  1. 아두이노 젯슨에 연결된 카메라를 통해 정류장으로 진입하는 영상을 촬영한다.\n
  2. 젯슨의 docker container에 있는 yolov5 모델을 이용하여 버스 번호를 detection한다.\n
  3. pyserial 라이브러리를 활요하여 젯슨에서 아두이노로 시리얼 통신을 통해 detection된 데이터를 전송한다.\n
  4. 아두이노에서 수신한 데이터에 맞는 버스 번호를 mp3 모듈을 통해 출력한다.\n
  5. 이용자는 아두이노에 있는 이어폰 단자를 이용하여 간편하게 버스 번호를 알려주는 음성 정보를 얻는다.\n


# 프로젝트 선정 동기 


# 실행 명령어
```
!python3 detect.py --werights best.pt --source <img, video, webcam, youtube link> 
```

## Acknowledgement
```
"본 연구는 과학기술정보통신부 및 정보통신기획평가원의 SW전문인재양성사업의 연구결과로 수행되었음"(2022-0-01127)
```
