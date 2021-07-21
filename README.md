### classification_project_1_airbnb_users

### 프로젝트의 목적
![image](https://user-images.githubusercontent.com/79970424/126503823-2bc179f6-7366-498b-90b1-8962e8d042d7.png)
- 2021년에 에어비엔비가 발표한 유연한 검색을 하기위해 어떤 준비를 했을까
- 에어비엔비가 케글에 올린 5년전 데이터 분석 대회에서 답을 찾을 수 있다
- 에어비엔비에서 데이터를 중요하게 여기고 빠르게 분석해서 마케팅에 사용하려는 뜻을 확인 할 수 있다
- 실제 어떤 데이터이고, 어떤 마케팅적 결론이 나올 수 있는지 알아보자
---
### 데이터 소개
![image](https://user-images.githubusercontent.com/79970424/126504318-2c2a446e-0d00-41cd-be77-505f7f8cc4f1.png)
- Age_gender_bkts : 나라의 연령별, 인구수 분포 데이터
- Countries : 나라의 정보, 위도, 경도, 언어
- Train_users : 학습데이터
- Test_users : 시험데이터
- Sample_submission : 제출양식

![image](https://user-images.githubusercontent.com/79970424/126504608-62eead36-5742-49f2-90ad-dd4ce6f7fc2b.png)
- 학습 데이터의 컬럼들과 결측치

![image](https://user-images.githubusercontent.com/79970424/126504755-361e879b-b73c-4cd8-a675-bcbcf966f265.png)
- 유저 세션데이터의 컬럼들과 결측치
---

### 과정
![image](https://user-images.githubusercontent.com/79970424/126505215-dc46dda1-14aa-45e6-8886-67bd73faf325.png)

---

### EDA
![image](https://user-images.githubusercontent.com/79970424/126505320-0e466cda-1c7f-4bb9-a042-b941a9d96579.png)
- Unknown, other 값이 많음
- 전체 데이터의 44%가 Unknown, other

![image](https://user-images.githubusercontent.com/79970424/126505457-a0e2739b-1c4c-4e80-8cec-cc5f4fe2c3cf.png)
- 0세부터 100세 이상의 이상치들이 많음
- 2014, 2013값도 존재
- 미국 기준 자동차 면허 소지기능나이인 16세부터 100세까지 제한 진행

![image](https://user-images.githubusercontent.com/79970424/126505739-73874c45-5c35-4d8f-af85-672fe9ad1aed.png)
- 기본 에어비엔비가 제일 많고 Facebook이 그 다음으로 많다

![image](https://user-images.githubusercontent.com/79970424/126505846-6e87213f-faa4-43b2-9b44-b0963261c825.png)
- 웹을 사용하는 유저가 많다

![image](https://user-images.githubusercontent.com/79970424/126505896-9c978c6b-cd79-4976-a6b5-7f1cc82cf817.png)
- 데스크탑을 사용하는 유저가 많다

![image](https://user-images.githubusercontent.com/79970424/126505941-6843547d-9010-497a-a57e-902faf5a5887.png)
- 크롬브라우저가 강세를 보임

![image](https://user-images.githubusercontent.com/79970424/126506013-dc49dfa3-a0e7-40a6-af84-04f87af2c230.png)
- 타겟 컬럼
- NDF가 너무 많다, 전체 데이터의 58%가 데이터가 없음
---

### 전처리
![image](https://user-images.githubusercontent.com/79970424/126506247-064fa92a-d3c5-4b29-b9f6-20cefba7d47b.png)
- Unknown, other를 other로 통합
- 연령의 걸측치를 연령의 중간값인 34로 대입
- 첫 부킹 날짜를 no, yes로 범주화
- 범주형 데이터의 전처리

![image](https://user-images.githubusercontent.com/79970424/126506414-766502fc-cad5-4427-8bc7-0ac1e09e0b2b.png)
- 세션 데이터를 학습데이터와 합칠 수 있게 전처리

![image](https://user-images.githubusercontent.com/79970424/126506944-3806ee5d-6b82-46c8-9479-a266897340af.png)
- 최종 전처리된 학습 데이터

---
### 첫 여행지 예측하기
![image](https://user-images.githubusercontent.com/79970424/126507452-097e9e3c-b2aa-4cb1-bfcd-2b632755b472.png)
- Baseline 설정

![image](https://user-images.githubusercontent.com/79970424/126507588-ebd41944-a7c3-4ea5-978a-7e0cabd54e92.png)
- 모델 정확도 70%

![image](https://user-images.githubusercontent.com/79970424/126507654-f719bee8-60d7-4444-a122-00f8d0e97d1b.png)
- feature importance 확인

![image](https://user-images.githubusercontent.com/79970424/126507688-899d342c-50d7-45b4-8033-2f01d8586847.png)
- feature importance가 0인 필요없는 컬럼 삭제

![image](https://user-images.githubusercontent.com/79970424/126507820-0f1a840a-fa7c-4b2e-9cdf-8e1a5c5ead3f.png)
- shap을 활용하여 인사이트 도출
- 예를 들어 캐나다로 여행을 가는 사람들은 에어비엔비로 가입한 유저들이다(signup_method_basic)
- 따라서 마케팅적으로 에어비엔비로 가입하는 신규 유저들에게 캐나다 광고를 띄워주면 예약률이 올라갈 것이다.

---
### 여행을 갈지 안갈지 예측하기(여행 실행 예측)
![image](https://user-images.githubusercontent.com/79970424/126508174-bb14761e-ad65-40d2-b777-818bd9f50761.png)
- 예약이 없는 유저들이 61%로 더 많다

![image](https://user-images.githubusercontent.com/79970424/126508271-cd451815-c4d6-46d3-a165-1421b4dd204c.png)
- 모델 정확도 77%
- Baseline 넘음

![image](https://user-images.githubusercontent.com/79970424/126508347-df6f8021-e641-4063-986c-94cc3970cd33.png)
- Feature importance 확인
- age가 높은데 중앙값으로 넣었기 때문인지 확인 필요

![image](https://user-images.githubusercontent.com/79970424/126508431-7e5eaace-273a-4627-b7cd-a1fe32185801.png)
- age결측치를 제거하고 새로 모델링
- 모델 정확도 71%
- Baseline 넘음

![image](https://user-images.githubusercontent.com/79970424/126508524-ceadcfd6-56f2-4006-8f0a-b90f87e56b13.png)
- Feature importance 재확인
- age가 내려가고 signup_method_facebook이 올라옴

![image](https://user-images.githubusercontent.com/79970424/126508602-99465811-5c2a-462f-bbd1-c7528344ac0a.png)
- shap을 활용하여 인사이트 도출
- 이진 분류의 경우 영향력이 같게 나타남

![image](https://user-images.githubusercontent.com/79970424/126508693-ae7f3413-b964-48ed-8afb-79ad575893a7.png)
- signup_method_facebook을 살펴보면 페이스북으로 가입한 유저들이 여행을 비교적 가지 않는다
- 따라서 마케팅적으로 페이스북이 아닌 다른 경로로 유저를 가입시키는 것이 유리하다
- 또는 페이스북의 가입 과정을 다른 경로의 가입 과정으로 바꿔주는 시도도 필요

![image](https://user-images.githubusercontent.com/79970424/126508962-90973b41-5753-4980-9557-3822015fae5b.png)
- action_requested를 살펴보면 실제 예약을 진행한 유저들은 action_requested에 체류한 평균적 시간이 압도적으로 크다
- 마케팅적으로 action_requested에 많이 체류하는 것이 유리하다

---
### 결론
- 에어비엔비는 데이터 모델링, 분석을 통해 인사이트를 도출하여 홈페이지를 수정하거나, 타겟별 광고유형을 변경했을 것으로 예상된다
- 그리고 5년 후인 지금 완성된 시스템을 통해 앱을 새롭게 런칭한 것으로 보인다
