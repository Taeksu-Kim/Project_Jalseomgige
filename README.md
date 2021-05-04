# 잘섬기게 프로젝트   

[![output 4points](http://img.youtube.com/vi/UFJKNmRXnVA/0.jpg)](https://youtu.be/UFJKNmRXnVA)   
이미지 클릭시 유튜브 동영상으로 링크됩니다.

# 프로젝트 내용   

### 낙상 방지 알람
1. Yolact 모델을 통해 침대 영역 인식, 침대 영역 좌표 추출   
2. Openpose로 양쪽 엉덩이, 양쪽 무릎 포인트의 좌표 추출
3. 양쪽 엉덩이 좌표 값이 침대 영역 안(침대 안의 사람으로 한정) and 한쪽 무릎의 키포인트라도 침대 영역 밖으로 나갈시 카운트
4. 카운트가 기준 값을 넘을시 낙상 위험 경고

![낙상방지 알고리즘](https://user-images.githubusercontent.com/63130907/116948669-018fdf80-acbb-11eb-8805-b0dbad614805.jpg)


### 욕창 방지 알람
1. Openpose로 양쪽 어깨, 목, 코의 좌표 추출
2. 양쪽 어깨와 목,코 간의 거리를 유클리디안 거리를 활용하여 계산   
3. 양쪽 어깨간의 거리가 목,코 간의 거리 * 임의의 숫자를 계산한 값과 비교하여 측면, 비측면으로 구분   
4. 측면일 경우 코와 목의 x좌표 값을 비교하여 왼쪽, 오른쪽 구분
5. 비측면일 경우 양쪽 어깨의 x좌표 값을 비교하여 앞쪽, 뒤쪽 구분
6. 한쪽 방향으로 일정이상 있을 시 자세 변경 경고

![욕창방지 알고리즘 ](https://user-images.githubusercontent.com/63130907/116949988-b081ea80-acbe-11eb-8818-1df8a8ded829.jpg)
![자세 샘플](https://user-images.githubusercontent.com/63130907/116949772-2174d280-acbe-11eb-9a2b-16c80bea8cf4.jpg)



# 파일 설명   
proto_final.py : 실행파일(침대 영역 세팅, 실시간, 비디오를 이용한 낙상,욕창 위
험 탐지, 알람)   
proto_test2.py : 샘플용 실행파일(침대 대신 컵, 오른 손목 포인트를 이용한 알람, 방향변경 알람의 기준시간이 더 짧음)   
eval.py : Yolact 원본 실행파일. https://github.com/dbolya/yolact  를 참고하여 실행인자 입력시켜줘야 함   
# 튜닝 파트   
src/util.py를 참고하여 실행 파일 내에서 받아와서 사용하는 값. (신체 포인트 좌표)   
data/config.py를 참고하여 실행 파일 내에서 사용하는 값. (Yolact 인식 객체별 index, 객체명) 

# 구동 환경 구축   
### Openpose 환경 구축:   
CUDA가 빌드된 Opencv가 없으면 코드 실행은 되지만 Openpose에서 상당한 끊김이 있으므로 GPU사용이 가능한 Opencv 환경 준비   
https://github.com/Hzzone/pytorch-openpose 의 model 폴더 안에 있는 파일들을 이 프로젝트의 model 폴더 안에 넣어줌(Openpose의 모델파일들임)

### Yolact 환경 구축:
https://github.com/dbolya/yolact 를 참고하여 구축.   
환경 구축 중 에러가 날 경우 참고 자료에 있는 일본 블로그들 참고. 구글 번역기를 이용하면 어느정도 이해가 가능함


# 참고 자료   
Yolact  https://github.com/dbolya/yolact   
Openpose  https://github.com/Hzzone/pytorch-openpose   
Windows 환경에서 Yolact 구동 환경 구축 일본 블로그  https://aulta.co.jp/archives/8262   
Yolact 구동 환경 중 DCNv2 오류 해결 일본 블로그  https://note.com/thedesignium/n/n0ba51afe9776   
Yolact 구동 환경 중 coco api 설치 에러 해결 블로그 http://blog.livedoor.jp/tmako123-programming/archives/51025848.html   

