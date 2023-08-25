# AI를 통한 시각장애인 대중교통 접근성 향상 프로젝트

🛠️
Stack
<img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=PyTorch&logoColor=white"><img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=Python&logoColor=white"><img src="https://img.shields.io/badge/opencv-5C3EE8?style=for-the-badge&logo=opencv&logoColor=black"><img src="https://img.shields.io/badge/linux-FCC624?style=for-the-badge&logo=linux&logoColor=black">

## :computer: 시연 자료
1️⃣버스 번호 추론
![image](https://github.com/K-Software-BootCamp/2023KEB_Murado-Ssul-Ja/assets/108107570/b38f67d5-99b2-4821-b971-102ebddc6eef)
2️⃣원본사진 -> 흑백 -> 이진화
![image](https://github.com/K-Software-BootCamp/2023KEB_Murado-Ssul-Ja/assets/108107570/a411b59b-2423-40be-a90a-75347a14a1b6)
3️⃣버스 번호 출력
![image](https://github.com/K-Software-BootCamp/2023KEB_Murado-Ssul-Ja/assets/108107570/5b9aab3f-cee8-42c6-ad8b-5580cace3897)


## ♻️프로젝트 흐름도
<img width="505" alt="image" src="https://github.com/K-Software-BootCamp/2023KEB_Murado-Ssul-Ja/assets/140637787/f5a5c66a-3be8-4296-8607-1a6d311cad27">

  :one: 아두이노 젯슨에 연결된 카메라를 통해 정류장으로 진입하는 영상을 촬영한다. \n

  :two: 젯슨의 docker container에 있는 yolov5 모델을 이용하여 버스 번호를 detection한다.
  
  3️⃣ pyserial 라이브러리를 활요하여 젯슨에서 아두이노로 시리얼 통신을 통해 detection된 데이터를 전송한다.
  
  4️⃣ 아두이노에서 수신한 데이터에 맞는 버스 번호를 mp3 모듈을 통해 출력한다.
  
  5️⃣ 이용자는 아두이노에 있는 이어폰 단자를 이용하여 간편하게 버스 번호를 알려주는 음성 정보를 얻는다.


## 💡프로젝트 선정 동기 

![image](https://github.com/K-Software-BootCamp/2023KEB_Murado-Ssul-Ja/assets/140637787/dfa1cdb4-e052-4992-b6c7-198d07259e2f)

위 자료에서 알 수 있듯이, 시각 장애인이 이용하기 가장 힘든 교통수단은 버스이며 그 이유는 그들이 버스 번호를 인식하기 힘들다는 것이다. 그래서, 우리는 AI와 기술을 통해 교통약자들의 문제를 해결하자는 목표를 갖고 해당 프로젝트 주제를 선정했다.

## 📖사용법
:one: BusNumber Detection 모델인 best.pt 파일과 BusNumberDetect.py 파일 다운로드
```
git clone git@github.com:K-Software-BootCamp/2023KEB_Murado-Ssul-Ja.git
```

:two: Yolov5 설치
```
git clone https://github.com/ultralytics/yolov5.git
cd yolov5
pip install -r requirements.txt
```

3️⃣ BusNumberDetect.py 파일과 best.pt 파일을 경로에 맞게 이동
```
mv ~/2023KEB_Murado-Ssul-Ja/BusNumberDetect.py /yolov5
mv ~/2023KEB_Murado-Ssul-Ja/best.pt /yolov5
```

4️⃣ 버스가 나오는 이미지나 유튜브 링크를 source로 사용하여 BusNumberDetect.py 실행
```
!python3 BusNumberDetect.py --werights best.pt --source <img, video, webcam, youtube link> 
```


### 🔸Acknowledgement
```
"본 연구는 과학기술정보통신부 및 정보통신기획평가원의 SW전문인재양성사업의 연구결과로 수행되었음"(2022-0-01127)
```
