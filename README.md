# Profiling ML Side Channel Attack on AES


## 부채널 분석이란?
암호 장비에서 암호 알고리즘 동작 시 발생하는 <b>부가적인 정보(소비전력, 전자기 신호 등)</b>를 수집 및 분석하여 비밀 정보를 획득하는 분석 기법
<img width="674" alt="스크린샷 2024-04-02 오전 1 34 00" src="https://github.com/grain-ahrok/PML_SCA_AES/assets/81209784/9b72ec42-9291-4ac0-8fe2-da24dde3d21b">


## 프로파일링 분석기법
전력 파형과 중간값 관계를 프로파일링하여 소수의 파형으로도 비밀값을 복구하는 기법 <br/>
<b>[프로파일링 단계]</b>
공격 대상 기기와 완전히 동일한 기기를 사용하여 중간값과 파형을 학습
<img width="1003" alt="스크린샷 2024-04-02 오전 1 39 40" src="https://github.com/grain-ahrok/PML_SCA_AES/assets/81209784/4ada48a2-5b73-4703-9dd6-8a1a8498f3c0">
<b>[비밀키 복구 단계]</b>
학습 모델을 통해 공격 대상 기기의 파형에 대응되는 중간값 예측
<img width="995" alt="스크린샷 2024-04-02 오전 9 03 45" src="https://github.com/grain-ahrok/PML_SCA_AES/assets/81209784/d3b25536-1fdf-4a67-ba04-98d702bd5211">


