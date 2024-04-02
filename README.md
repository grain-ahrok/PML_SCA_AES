# Profiling ML Side Channel Attack on AES


## 부채널 분석이란?
암호 장비에서 암호 알고리즘 동작 시 발생하는 <b>부가적인 정보(소비전력, 전자기 신호 등)</b>를 수집 및 분석하여 비밀 정보를 획득하는 분석 기법
<img width="674" alt="스크린샷 2024-04-02 오전 1 34 00" src="https://github.com/grain-ahrok/PML_SCA_AES/assets/81209784/9b72ec42-9291-4ac0-8fe2-da24dde3d21b">

<br/><br/>
## 프로파일링 분석기법이란?
전력 파형과 중간값 관계를 프로파일링하여 소수의 파형으로도 비밀값을 복구하는 기법 <br/><br/>
<b>[프로파일링 단계]</b></br>
공격 대상 기기와 완전히 동일하고 제어가능한 기기를 사용하여 중간값과 파형을 학습
<img width="674" alt="스크린샷 2024-04-02 오전 1 39 40" src="https://github.com/grain-ahrok/PML_SCA_AES/assets/81209784/4ada48a2-5b73-4703-9dd6-8a1a8498f3c0">
<br/><br/>
<b>[비밀키 복구 단계]</b></br>
학습 모델을 통해 공격 대상 기기의 파형에 대응되는 중간값 예측
<img width="674" alt="스크린샷 2024-04-02 오전 9 03 45" src="https://github.com/grain-ahrok/PML_SCA_AES/assets/81209784/d3b25536-1fdf-4a67-ba04-98d702bd5211">

<br/><br/>
## SPA(Simple Power Analysis)
암호화 과정의 1라운드 전력 파형임을 알고 있을때, 4부분으로 나뉘어지고 첫번째, 두번째는 비슷한 파형이 16번 반복되고 4번째 부분은 비슷한 파형이 4번 반복되는 것을 보고 AES 파형임을 유추할 수 있다.
<img width="1172" alt="스크린샷 2024-04-02 오전 10 17 53" src="https://github.com/grain-ahrok/PML_SCA_AES/assets/81209784/44117b34-fdd6-4b83-9740-f8fb3fe82b7a">

<br/><br/>
## 프로파일링 단계
임의의 키와 임의의 평문을 암호화시 발생하는 전력파형을 중간값으로 라벨링한다. 선형함수를 사용하는 경우 정확도가 떨어지므로, 비선형함수인 S-Box를 사용해서 인공지능 모델을 학습한다.<br/>
데이터: 𝑆𝑏𝑜𝑥 연신 시 전력 파형 <br/>
라벨 : 𝑆𝑏𝑜𝑥( 𝑘𝑒𝑦 ⨁ 𝑝𝑡 ) 


<br/><br/>
## 비밀키 복구 단계
임의의 평문을 암호화시 발생하는 전력파형을 통하여 고정 비밀키를 알 수 있다.


<br/><br/>
## 결과
학습데이터 7000set
검증데이터 3000set
테스트데이터 3000set <br/>
<img width="674" alt="스크린샷 2024-04-02 오전 1 34 00" src="https://github.com/grain-ahrok/PML_SCA_AES/assets/81209784/64bf62b9-0899-44a2-8378-143b30a75459"> <br/>
loss: 1.1462 - accuracy: 0.6241 - val_loss: 0.2748 - val_accuracy: 0.9477 <br/><br/>

<img width="674" alt="스크린샷 2024-04-02 오전 1 34 00" src="https://github.com/grain-ahrok/PML_SCA_AES/assets/81209784/51c03a42-56ef-43ea-a134-b26532dc6023"> <br/>
right key:  0x2b <br/>
key counts:  521





