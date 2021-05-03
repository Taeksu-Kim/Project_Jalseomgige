# 잘섬기게 프로젝트   

# 파일 설명   
proto_final.py : 실행파일(침대 영역 세팅, 실시간, 비디오를 이용한 낙상,욕창 위험 탐지, 알람)   
proto_test2.py : 샘플용 실행파일(침대 대신 컵, 오른 손목 포인트를 이용한 알람, 방향변경 알람의 기준시간이 더 짧음)   
eval.py : Yolact 원본 실행파일. https://github.com/dbolya/yolact  를 참고하여 실행인자 입력시켜줘야 함   
# 튜닝 파트   
src/util.py를 참고하여 실행 파일 내에서 받아와서 사용하는 값. (신체 포인트 좌표)   
data/config.py를 참고하여 실행 파일 내에서 사용하는 값. (객체별 index, 객체명) 

# 구동 환경 구축:   
1. Openpose 환경 구축   
CUDA가 빌드된 Opencv가 없으면 코드 실행은 되지만 Openpose에서 상당한 끊김이 있으므로 GPU사용이 가능한 Opencv 환경 준비   
https://github.com/Hzzone/pytorch-openpose 의 model 폴더 안에 있는 파일들을 이 프로젝트의 model 폴더 안에 넣어줌(Openpose의 모델파일들임)

2. Yolact 환경 구축
https://github.com/dbolya/yolact 를 참고하여 구축.
환경 구축 중 에러가 날 경우 참고 자료에 있는 일본 블로그들 참고. 구글 번역기를 이용하면 어느정도 이해가 가능함.

# 참고 자료   
Yolact  https://github.com/dbolya/yolact   
Openpose  https://github.com/Hzzone/pytorch-openpose   
Windows 환경에서 Yolact 구동 환경 구축 일본 블로그  https://aulta.co.jp/archives/8262   
Yolact 구동 환경 중 DCNv2 오류 해결 일본 블로그  https://note.com/thedesignium/n/n0ba51afe9776   
Yolact 구동 환경 중 coco api 설치 에러 해결 블로그 http://blog.livedoor.jp/tmako123-programming/archives/51025848.html   
