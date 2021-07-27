# MyBanking
open banking api를 활용한 내 계좌 관리 앱

# 구성도
![구성도](https://user-images.githubusercontent.com/49589578/127088563-003921bf-9d64-4889-a045-add85d3d5d9d.JPG)

# 개발 일지 

## One Activity, Multi Fragment 구조
- 사이드메뉴, 액션바 등을 하나의 Activity에서 계속 유지하면서 Fragment만 교체하면 좀 더 가볍게 구동할 것이라는 아이디어에서 설계

## event bus의 도입
- Activity가 Fragment를 member 로 포함하는 구조(혹은 그 역의 구조)에서는 모듈 간 결합도가 높아지는 문제가 발생하므로, 
  비동기 이벤트 메시지 처리를 통해 각 모듈 간 결합도를 낮춰봄

## 공통 WebView fragment 사용
- 사용자인증 계열 화면에서 호출하는 WebView는 하나의 공통 Fragment 로 생성하여, 파라미터만 바뀌는 형식으로 재사용
 
 
## Retrofit library 도입 및 추상화
- low-level의 I/O 처리를 library에 맡기고, 추상화를 통해 호출구조를 단순화.

## Constants.java
- 설정화면에 출력되는 기본값은 Constants.java에 정의된 기본값임. 이후 사용자가 수정한 화면의 폼 데이터는 사용자의 저장액션에 의해 SharedPreferences 에 저장되는 구조임

## 중복되는 화면 공통화
 - 사용자인증 개선버전과 계좌등록확인 개선버전은 입력 파라미터의 형태가 동일하므로 하나의 화면 폼을 공유해서 사용하며, 파라미터를 통해서 버튼명, 메뉴명만 교체하여 사용함.
 
 
## 뒤로가기
- 뒤로가기에 대한 처리는 각 Fragment에서 목적지를 결정하여 코딩하도록 처리함


## 문제점
- okhttp3 라이브러리를 이용하여 통신을 하는데 버전이 올라가면서 몇몇 메소드들이 사라진 것 같아서 그 기능을 사용하지 못하는 중.. stack overflow에서도 이와 같은 문제를 가진 사람
  들이 있는데 아직 해결된 사람이 없음 -> 다른 방식으로 통신 처리를 해야할지 고민 중
  
- open banking api 참조문서와 테스팅 샘플 코드를 이용하여서 결과를 액티비티에 뿌려줄 때 json형태로 받아오기 때문에 UI 적으로 깔끔하지 않음 -> DB에 저장하고 그것을 데이터로 가공하여
  호출할 예정
  

# 구현 화면
![1](https://user-images.githubusercontent.com/49589578/127088566-38c8dba1-c2bc-4f86-906e-ba4c2350becf.JPG)
![2](https://user-images.githubusercontent.com/49589578/127088567-6c2c172d-40a1-4d47-a3ef-df122cfc7166.JPG)
