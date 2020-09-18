# youtube_search 사용하는 방법
- 이미지 크기가 보기 '불편'할 수 있습니다. 이미지 크기 문제는 천천히 해결하겠습니다.

## 1. youtube api 키 받아오기

### 1.1. 구글 개발자 콘솔 
[구글 개발자 콘솔](https://console.developers.google.com/)에서 프로젝트를 생성합니다. 최초 접속 시 대시보드에 '이 페이지를 보려면 프로젝트를 선택하세요.'라는 메시지가 보일 것입니다. 오른쪽에 보이는 프로젝트 만들기를 누르세요.
![](https://user-images.githubusercontent.com/16553217/93542668-97793300-f994-11ea-9923-3aa9b7f81ab9.png)

### 1.2. 프로젝트
프로젝트 이름 아무렇게나 만들어 주세요.
![](https://user-images.githubusercontent.com/16553217/93542758-c7283b00-f994-11ea-8bf5-a5bfeb8b5cf8.png)

### 1.3. 구글 개발자 콘솔 - 대시보드
그러면 1.1의 [구글 개발자 콘솔 > 대시보드]에 'API가 없다'는 메시지가 나타납니다. 'API 라이브러리' 링크를 눌러 이동합니다.
![](https://user-images.githubusercontent.com/16553217/93542857-0d7d9a00-f995-11ea-9dd0-f351c2572a57.png)

### 1.4. API 라이브러리
'youtube'라고 검색하면 'Youtube Data API v3'가 나타납니다. 검색 후 누릅니다. 이후 나타나는 화면에서 <사용>을 누릅니다.
![](https://user-images.githubusercontent.com/16553217/93543735-51719e80-f997-11ea-8a64-1805b65050fe.png)
![](https://user-images.githubusercontent.com/16553217/93543933-bf1dca80-f997-11ea-8392-f48518b124ee.png)

### 1.5. API 및 서비스
<사용자 인증 정보 만들기>를 누릅니다. 그런 다음 '사용자 인증 정보'에서 다음과 같이 동일하게 설정합니다. <어떤 사용자 인증 정보가 필요한가요?>를 누르면 API 키가 만들어집니다.
![](https://user-images.githubusercontent.com/16553217/93544041-060bc000-f998-11ea-8111-f5ef12ffb1ec.png)
![](https://user-images.githubusercontent.com/16553217/93544166-56831d80-f998-11ea-9be7-ac182768f110.png)

### 1.6. API 키 복사하기
'API 키' 항목에 있는 '키'를 복사합니다. <클립보드 복사> 버튼을 눌러 복사하세요(네모 2개 겹쳐진 것임).
![](https://user-images.githubusercontent.com/16553217/93544240-87635280-f998-11ea-81f6-8ba4a9054ac6.png)

## 2. 코드 열고 youtube api 키 입력하기

### 2.1. 코드에 api 키 입력하기
코드를 열고 api 키를 입력하세요. 코드에서 `DEVELOPER_KEY` 항목에 문자열로 api 키를 입력하면 됩니다.

```
(...생략...)

"""
    주의!
    1. DEVELOPER_KEY 절대 외부에 노출하지 마세요.
"""
DEVELOPER_KEY = "PLEASE ADD DEVELOPER KEY"
YOUTUBE_API_SERVICE_NAME = "youtube"
YOUTUBE_API_VERSION = "v3"
FREEBASE_SEARCH_URL = "https://www.googleapis.com/freebase/v1/search?%s"

(...생략...)

```

### 2.2. 크롤링 범위 설정하기
크롤링 범위 설정을 위해서는 `search_counter in range(1, 6):`의  `range(1, 6)`의 숫자에서 2번째 매개변수값을 바꾸면 됩니다. 숫자 1단위가 50개의 항목을 의미합니다. 예를 들어 `range(1, 2)`라고 하면 50개의 데이터만 가져옵니다.

```
(...생략...)

for search_counter in range(1, 6):

(...생략...)
```

### 2.3. 코드 실행하고 키워드 입력하기 

파일이 있는 폴더에서 `python` 명령어로 파일을 실행하면 아무것도 진행되지 않는 것처럼 보일 것입니다. 키워드 입력을 기다리는 거죠. 키워드를 아무렇게나 입력하고 `Enter`
를 누르면 정보 수집이 시작됩니다.

> 주의! python 패키지가 설치되어 있지 않으면 코드가 실행되지 않습니다. 이 코드 실행을 위해 필요한 패키지는 다음과 같습니다.

- python 3.8 기준입니다.
- pip install apiclient
- pip install --upgrade google-api-python-client
- pip install oauth2client
- pip install openpyxl
