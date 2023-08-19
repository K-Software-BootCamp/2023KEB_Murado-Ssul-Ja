# AI를 통한 시각장애인 대중교통 접근성 향상 프로젝

![image](https://github.com/K-Software-BootCamp/2023KEB_Murado-Ssul-Ja/assets/108107570/bb25f83b-5842-4663-bee1-76c31e370f03)


This app was built with the purpose of bus delay prediction. For bus detection at the bus stop Kuchyňka webcam provided by KFA MFF CUNI is used. Docker container ffmpeg fetches .m3u8 stream and saves .jpg files into shared img/ folder. Data_handler container waits for new images to be present and feeds them via POST request to a fitted model. In the model container there is a preloaded model.pkl with serving Flask API. For the model we used feature extraction, PCA and LinearSVC. More in train.ipynb. 

Model uses 20 features and has 89% score in 3-fold testing.

### Installation
For running Jupyter notebooks first install packages
```shell
python3 -m pip install -r requirements.txt
```
To run these docker containers run
```shell
docker-compose run --build
```

### Training
Uncropped labelled images are available [here](https://drive.google.com/file/d/1TGTDeiSkq6p9aFNulstceOA2dSqNKwyh/view?usp=sharing) and cropped images are available [here](https://drive.google.com/file/d/1ztelW58MWQgLfUvbT-uhiYtzNCWoSNcG/view?usp=sharing). For training use example in `train.ipynb`.

### Links
https://kfa.mff.cuni.cz/?page_id=1102

https://www.dpp.cz/aktualni-odjezdy?cis=58806&ds=Kuchy%C5%88ka

### Example output
```shell
data_handler_1  | sending request ... 
model_1         | 172.25.0.3 - - [15/Apr/2021 17:57:31] "POST / HTTP/1.1" 200 -
data_handler_1  | {'time': '18:57:06\n\x0c', 'value': 0}
ffmpeg_1        | frame=   31 fps=0.4 q=2.0 size=N/A time=00:01:56.00 bitrate=N/A dup=0 drop=1156 speed[http @ 0x8afbc0] Opening 'http://kfa.mff.cuni.cz/streaming/north.m3u8' for reading
ffmpeg_1        | [http @ 0x8a7280] Opening 'http://kfa.mff.cuni.cz/streaming/north4.ts' for reading
ffmpeg_1        | [hls,applehttp @ 0x7def80] Opening 'http://kfa.mff.cuni.cz/streaming/north4.ts' for reading
data_handler_1  | sending request ... 
model_1         | 172.25.0.3 - - [15/Apr/2021 17:57:41] "POST / HTTP/1.1" 200 -
data_handler_1  | {'time': '18:57:14\n\x0c', 'value': 0}
data_handler_1  | sending request ... 
model_1         | 172.25.0.3 - - [15/Apr/2021 17:57:41] "POST / HTTP/1.1" 200 -
data_handler_1  | {'time': '18:57:18\n\x0c', 'value': 0}
ffmpeg_1        | frame=   34 fps=0.4 q=2.0 size=N/A time=00:02:08.00 bitrate=N/A dup=0 drop=1253 speed[http @ 0x7e8c80] Opening 'http://kfa.mff.cuni.cz/streaming/north.m3u8' for reading
ffmpeg_1        | [http @ 0x8afa00] Opening 'http://kfa.mff.cuni.cz/streaming/north5.ts' for reading
ffmpeg_1        | [hls,applehttp @ 0x7def80] Opening 'http://kfa.mff.cuni.cz/streaming/north5.ts' for reading
data_handler_1  | sending request ... 
model_1         | 172.25.0.3 - - [15/Apr/2021 17:57:51] "POST / HTTP/1.1" 200 -
data_handler_1  | {'time': '18:57:26\n\x0c', 'value': 1}
data_handler_1  | sending request ... 
model_1         | 172.25.0.3 - - [15/Apr/2021 17:57:51] "POST / HTTP/1.1" 200 -
data_handler_1  | {'time': '18:57:30\n\x0c', 'value': 1}
data_handler_1  | sending request ... 
model_1         | 172.25.0.3 - - [15/Apr/2021 17:57:51] "POST / HTTP/1.1" 200 -
data_handler_1  | {'time': '18:57:22\n\x0c', 'value': 1}
ffmpeg_1        | frame=   36 fps=0.4 q=2.0 size=N/A time=00:02:16.00 bitrate=N/A dup=0 drop=1351 speed[http @ 0x875900] Opening 'http://kfa.mff.cuni.cz/streaming/north.m3u8' for reading
ffmpeg_1        | [http @ 0x8771c0] Opening 'http://kfa.mff.cuni.cz/streaming/north6.ts' for reading
ffmpeg_1        | [hls,applehttp @ 0x7def80] Opening 'http://kfa.mff.cuni.cz/streaming/north6.ts' for reading

```
