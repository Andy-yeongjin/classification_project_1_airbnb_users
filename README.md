### classification_project_1_airbnb_users

## 데이터 분석, 분포 확인
![image](https://user-images.githubusercontent.com/79970424/126075109-84b3d953-3382-4df9-847a-c5f0a7738277.png)
- Unknown, Other값이 44%

![image](https://user-images.githubusercontent.com/79970424/126075124-39e1e8e8-d451-4186-9639-2fe5f1d3a45b.png)
- 연령분포가 0세도 많고, 100세 이상도 많음
- 2014, 2013도 존재

![image](https://user-images.githubusercontent.com/79970424/126075138-7cf345a1-62ab-45f5-a826-b020614688ff.png)
- Facebook으로 가입한 유저들이 많음

![image](https://user-images.githubusercontent.com/79970424/126075146-f560e70c-466e-485d-b9d2-e28083fef55b.png)
- 웹을 사용해서 가입한 유저들이 많음
- 5년전 데이터이기 때문, 최근 데이터들은 모바일이 많을 것으로 예상

![image](https://user-images.githubusercontent.com/79970424/126075163-1b2ae503-12b6-4788-b786-8b1e8429025c.png)
- 크롬 브라우져를 사용하는 유저들이 많음

![image](https://user-images.githubusercontent.com/79970424/126075171-4234cc24-3dc8-430a-8f87-322cd72c960b.png)
- 출발을 안한 사람 (NDF), 기타 지역 (other)이 많다
- NDF 58%
---

## 전처리
![image](https://user-images.githubusercontent.com/79970424/126075204-91f750b4-f23b-4dbf-8b70-fabacc1785b0.png)
- Unknown, Other을 Other로 처리
- 나이의 결측치에 중앙값 사용
- 범주형 데이터 전처리

![image](https://user-images.githubusercontent.com/79970424/126075218-89ea1d07-2600-4ada-ae14-be4ee61c3e0e.png)
- 세션 데이터를 합치기 쉬운 형태로 변환

![image](https://user-images.githubusercontent.com/79970424/126075225-2bf2eedf-02b1-4d09-8e15-46dfebb9e3b8.png)
- 전처리한 새로운 train 데이터

---
## 목적지 예측 모델
![image](https://user-images.githubusercontent.com/79970424/126075255-b183cd3f-049e-40df-8e62-17acb1b9cae1.png)
- 모델의 Baseline 설정

![image](https://user-images.githubusercontent.com/79970424/126075269-c9ca56ea-11cb-43de-aad5-9833af33521b.png)
- 모델 정확도 70%

![image](https://user-images.githubusercontent.com/79970424/126075279-ea8f4949-2ec4-4a8a-a0b9-dedb93d4dd1a.png)
- Feature importance 확인

![image](https://user-images.githubusercontent.com/79970424/126075286-59b22f7e-4d31-495a-ba9c-91136e04e87f.png)
- Feature importance가 0인 218개의 컬럼 제거후 모델링
- 정확도는 같다

![image](https://user-images.githubusercontent.com/79970424/126075306-fc4f8b2e-9e10-4770-9549-57f84c43d29f.png)
- 최종 Feature importance
- 목적지 예측 모델에 가장 영향을 많이 준 행동은 action_acculynk_pin_pad_success

---
## 여행 실행 예측 모델
![image](https://user-images.githubusercontent.com/79970424/126075347-ca2016f4-425f-434e-8a74-7bb8fd8c0568.png)
- Baseline 설정
- 예약이 없는 유저 61%

![image](https://user-images.githubusercontent.com/79970424/126075372-6d04e2ab-028b-4804-a8df-5a40f64ba52a.png)
- 모델 정확도 77%

![image](https://user-images.githubusercontent.com/79970424/126075392-c6eccc84-8025-43ee-9666-60c9f252f172.png)
- Feature importance 확인
- 여행 실행에 가장 영향을 많이 준 컬럼은 Age
- 혹시 초기에 Age의 결측치를 중앙값으로 넣어서 영향을 많이 준건지 재확인 필요

![image](https://user-images.githubusercontent.com/79970424/126075458-ded9a98d-4ede-4a11-857d-fae8a384652f.png)
- Age의 결측치를 제거하고 재모델링
- 정확도는 6% 떨어짐

![image](https://user-images.githubusercontent.com/79970424/126075483-6f185b02-00ca-45a2-b8d9-a519f4861543.png)
- 다시 Feature importance를 확인
- 그래도 Age가 가장 영향을 많이 줌

![image](https://user-images.githubusercontent.com/79970424/126075508-53a96d03-32bb-45d0-a0ff-81e0896f9367.png)
- 여행을 실행한 유저와 실행 안한 유저의 Age 분포를 확인
- 분포 모양은 같다
- 인원만 여행을 실행한 유저가 많음

![image](https://user-images.githubusercontent.com/79970424/126075530-acb4bd7e-df24-47f0-8e3a-f4e6a7c6321b.png)
- 여행을 실행한 유저들은 Action_show 행동을 많이 보여줌
- 여행을 실행하지 않은 유저들은 Action_update 행동을 많이 보여줌
- 마케팅 할 시 고려요인
