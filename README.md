<h1 align="center">
  Stipop
  <br>
</h1>


<h4 align="center">Generate revenue and propel user engagement with Stipop Store API</h4>

<p align="center">
  <a href="#Intro">Intro</a> •
  <a href="#Key-Features">Key Features</a> •
  <a href="#get-started-rocket">Get Started</a> •
  <a href="#announcements-loudspeaker">Announcements</a> •
  <a href="#opening-issues-warning">Issues</a> •
  <a href="#license">License</a>
	  <br>
  <a href="#1-package">1. Package</a> •
  <a href="#2-donwload-구매-정보">2. Download</a> •
  <a href="#3-analytics">3. Analytics</a> •
  <a href="#4-common">4. Common</a>
</p>



## Intro

![Works with Android](https://img.shields.io/badge/Works_with-Android-green?style=flat-square)
![Works with iOS](https://img.shields.io/badge/Works_with-iOS-blue?style=flat-square)
![Works with JavaScript](https://img.shields.io/badge/Works_with-JavaScript-red?style=flat-square)
![GitHub issues](https://img.shields.io/github/issues/stipop-development/Stipop_Sticker_API?style=flat-square)

> 스티팝 스티커 스토어 API를 통해 서비스에서 새로운 수익을 창출할 수 있습니다.

스티커는 가장 효과적이고 쉬운 감정표현이 가능합니다. 때문에 스티커는 온라인 이용자들에게 필수적인 요소입니다. 카카오톡에서만 사용되던 스티커를 당사 서비스에서 제공해보세요. 쉽고 빠른 설치를 통해 새로운 수익을 창출 할 수 있습니다. 저희는 스티커를 통해 이용자들이 온라인에서 더 효과적으로 커뮤니케이션 할 수 있도록 돕습니다. 

아래 API 문서는 '스티커 스토어' 설치를 위한 문서입니다. 스티커 스토어가 아닌 '일반 스티커' 설치는 <a href="https://github.com/stipop-development/Stipop_Sticker_API" target="_blank">여기서</a> 확인할 수 있습니다.

## Key Features
* 스티커 인기순위 조회
  - Pricing plan에 따라 20~3,000 패키지 리스트 조회
  - 키워드, 카테고리, 국가, 언어 등의 파라미터를 활용해 세밀한 스티커 리스트 조회 가능
  - 총 25개국 5,000명의 작가가 디자인한 스티커
* 다양한 언어 제공
  - English/Spanish/Hindi/Russian/German/French/Portuguese/Italian/Chinese/Catonese/Japanese/Thai/Indonesian/Korean
* 스티커 구매 정보
  - 쉬운 스티커 판매 모델을 적용한 빠른 개발 및 유료 스티커 수익화
* 스티커 전송 통계
  - 스티커 전송 통계를 통해 보다 세밀한 스티커 추천과 이를 통한 수익 극대화


## Get started :rocket:

아래 API Document를 통해 response 확인 및 서비스에 스티커 스토어를 적용할 수 있습니다. 개발 진행시 발생되는 에러/버그는 이슈에 등록해주시면 24시간 내로 응답됩니다. 새로 추가되는 업데이트는 하단 'Announcement'란에 명시됩니다. 추가 문의는 biz@stipop.io로 해주시기 바랍니다.

v0.1은 스티커 스토어 개발을 위한 기본 기능/스티커를 테스트 해볼 수 있는 버전입니다.  세부 기능은 지속적으로 추가될 예정입니다 (~07/07).
  1. 선물함
     - 받은 선물 리스트 
     - 보낸 선물 리스트 
  2. 좋아요
     - 내가 좋아요 한 이모티콘 리스트
  3. 최근 본 이모티콘 리스트 
  4. Setting
     - 내 이모티콘 순서 변경(키보드단에서 보이는 순서)
     - 내 이모티콘 숨김(키보드 단에서 안보이게/삭제 아님)


<h4 align="center">
  <br>
</h4>

# API Document

## 1. Package

### 1.1 Package Ranking List 스티커팩 인기순위 조회

스티커팩 인기순위 리스트는 적용된 Pricing Plan에 따라 20개 혹은 200개의 스티커를 불러올 수 있습니다. 스티팝에 업로드 된 모든 스티커는 전 세계 작가들이 제작한 스티커이며 승인되기 위해서는 스티팝 콘텐츠 가이드라인을 통과해야만 합니다. 디폴트로 적용된 인기순위는 스티팝 앱 내 데이터를 통해 정해진 순위이며 개발이 진행됨에 따라 당사 서비스 다운로드를 기준으로 순위가 정해질 수 있습니다. 

* **URL**

  /v0.1/store/package

* **Method:**

  `GET`
  
*  **Request Headers**

   **Required:**
 
   `apikey=[string]` Issued apikey value


* **Request Query Parameters**

  **Required:**
  
  `userId=[string]` 각 개별 사용자를 구분 할 수 있는 고유 값
  
  **Not Required:**
  
  `pageNumber=[int]` 페이지 번호
  
  `language=[string]` 스티커 언어팩 ex) English, Spanish, Korean, German, French, Japanese
  
  `date=[string]` 인기순위 기간  ex) Daily, Weekly, Monthly 미입력시 전체순위
  
  `category=[string]` 스티커 카테고리 x.x의 카테고리 조회후 검색
  
  `animated=[string]` Y: 움직이는 스티커 랭킹조회, N: 스티커 랭킹조회, 파라미터 미입력시 전체조회
  
  `country=[string]` 국가별 랭킹 두자리 국가코드 입력 ex) kr, us, es
  
  `searchText=[string]` 검색어

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** <br />
    ```json
    {
      "header": {
          "code": "0000",
          "status": "success",
          "message": "요청 성공"
      },
      "body": {
          "packageList": [
              {
                  "packageId": 2309,                             //스티커팩 아이디
                  "packageName": "cada día",                     //스티커팩 이름
                  "packageImg": "https://img....70AAeHBn4N.png", //스티커팩 대표 이미지
                  "packageCategory": "Animation/Cartoon,Gag",    //스티커팩 카테고리
                  "packageKeywords": "bonito,mono,bello,adorable,life,cute,lovely", //스티커팩 키워드
                  "packageAnimated": "N",                        //움직이는 스티커 여부
                  "isNew": "N",                                  //신규출시 여부
                  "artistName": "pinono",                        //작가 이름
                  "language": "Spanish",                         //언어
                  "isDownload": "Y"                              //구매 여부
              },
              {
                  "packageId": 2473,
                  "packageName": "¿Cómo estás?",
                  "packageImg": "https://img.....Ggdu7s3J15.gif",
                  "packageCategory": "Phrases,Etc.",
                  "packageKeywords": "¿Cómoestás?,letra",
                  "packageAnimated": "Y",
                  "isNew": "N",
                  "artistName": "annapig",
                  "language": "Spanish",
              },
              `......`
          ]
      }
    }
    ```
 
* **Error Response:**

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist apikey",
      "code": "9000"
    }
    ```
    OR

  * **Code:** 500 Internal Server error <br />
    **Content:** 
    ```json
    {
       "status" : "fail", 
       "message": "server error", 
       "code":"1000"
    }
    ```

* **Sample Call:**

  ```curl
  curl --location --request GET "https://bapi.stipop.io/store/v0.1/package?userId=xxx&pageNumber=1&country=kr" \ --header "apikey:xxxxxxxxx"
  ```
  

### 1.2 Package Info 스티커팩 상세

스티커는 팩으로 구성됩니다. 하나의 스티커 팩은 15~24개의 스티커를 가지고 있으며 스티커 팹 이름, 작가 정보, 스티커 정보, 대표 이미지 등으로 구성되어 있습니다. 스티커팩 상세 API를 통해 스티커 페이지를 만들어보세요.

* **URL**

  /v0.1/store/package/:packageId

* **Method:**

  `GET`
  
*  **Request Headers**

   **Required:**
 
   `apikey=[string]` Issued apikey value

* **Request Path Parameters**

  **Required:**
  
  `packageId=[int]` 패키지 아이디 값

* **Request Query Parameters**

  **Required:**
  
  `userId=[string]` 각 개별 사용자를 구분 할 수 있는 고유 값

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** <br />
    ```json
    {
      "header": {
          "code": "0000",
          "status": "success",
          "message": "요청 성공"
      },
      "body": {
          "package": {
            "packageId": 118,                       //패키지 아이디
            "artistName": "MightyCat",              //작가명
            "packageName": "Stuart",                //스티커팩 이름
            "packageImg": "https://img....png",     //스티커팩 대표 이미지 url
            "packageAnimated": "N",                 //움직이는 스티커 여부
            "packageCategory": "Animation/Cartoon", //스티커팩 카테고리 
            "packageKeywords": "Stuart,Sticker",    //스티커팩 키워드
            "isNew": "N",                           //신규출시여부
            "language": "English",                  //언어
            "isDownload": "Y",                              //구매 여부
            "stickers": [                           //스티커팩 스티커 리스트
                {
                    "stickerId": 790,               //스티커 아이디
                    "packageId": 118,               
                    "stickerImg": "https://img...._5_2.png" //스티커 이미지 url
                },
                {
                    "stickerId": 791,
                    "packageId": 118,
                    "stickerImg": "https://img....._6_1.png"
                }
                ......
            ]
        }
      }
    }
    ```
 
* **Error Response:**

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist apikey",
      "code": "9000"
    }
    ```
    OR

  * **Code:** 500 Internal Server error <br />
    **Content:** 
    ```json
    {
       "status" : "fail", 
       "message": "server error", 
       "code":"1000"
    }
    ```

* **Sample Call:**

  ```curl
  curl --location --request GET "https://bapi.stipop.io/store/v0.1/package/118?userId=9937&" \ --header "apikey:xxxxxxxxx"
  ```
  
## 2 Donwload 구매 정보
### 2.1 Download Sticker 스티커팩 구매정보 전달

사용자들은 스티커 스토어 API에서 제공되는 스티커를 구매해 사용 할 수 있습니다. 스티커 구매는 접속중인 서비스에서 인앱 결제 혹은 서비스의 내부 코인 시스템을 통해 구매가 이뤄집니다. 구매 완료된 스티커는 해당 API를 통해 다운로드 할 수 있으며 이때 가격 정보가 스티팝에 제공됩니다. 스티팝과 수익 분배는 월 기준으로 익월에 진행되며 이는 스티팝 대시보드 (준비중)에서 자동으로 진행됩니다.

* **URL**

  /v0.1/store/download/:packageId

* **Method:**

  `POST`
  
*  **Request Headers**

   **Required:**
 
   `apikey=[string]` Issued apikey value

* **Request Path Parameters**

  **Required:**
  
  `packageId=[int]` 패키지 아이디 값

* **Request Query Parameters**

  **Required:**
  
  `userId=[string]` 각 개별 사용자를 구분 할 수 있는 고유 값
  
  `price=[string]` 각 해당 서비스의 가격정보 전달
  
  **Not Required:**
  
  `country=[string]` 국가별 다운로드 집계를 위한 2자리 국가코드 ex) kr, us, es

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** <br />
    ```json
    {
      "header": {
          "code": "0000",
          "status": "success",
          "message": "요청 성공"
      },
      "body": []
    }
    ```
 
* **Error Response:**

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist apikey",
      "code": "9000"
    }
    ```
    OR

  * **Code:** 500 Internal Server error <br />
    **Content:** 
    ```json
    {
       "status" : "fail", 
       "message": "server error", 
       "code":"1000"
    }
    ```
    
* **Warning Response:**    
  
  * **Code:** 200  <br />
    **Content:** 
    ```json
    {
        "header": {
            "code": "0000",
            "status": "warning",
            "message": "중복 구매"
        },
        "body": []
    }
    ```

* **Sample Call:**

  ```curl
  curl --location --request POST "https://bapi.stipop.io/store/v0.1/download/118?userId=9937" \ --header "apikey:xxxxxxxxx"
  ```
  
### 2.2 Download History 구매 내역 조회

사용자의 스티커 구매 내역 조회를 통해 사용자의 device 변경 등의 상황에도 리스트를 기록해 보여줄 수 있습니다. 추후 업데이트 되는 0.2 버전에서는 구매한 스티커를 hide 하는 기능과 순서를 바꾸는 기능이 추가될 예정입니다. 

* **URL**

  /v0.1/store/download/:userId

* **Method:**

  `GET`
  
*  **Request Headers**

   **Required:**
 
   `apikey=[string]` Issued apikey value

* **Request Path Parameters**

  **Required:**
  
  `userId=[string]` 각 개별 사용자를 구분 할 수 있는 고유 값

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** <br />
    ```json
    {
      "header": {
          "code": "0000",
          "status": "success",
          "message": "요청 성공"
      },
      "body": {
        "packageList": [
            {
                "packageId": 118,
                "packageName": "Stuart",
                "packageImg": "https://img...._7.png",
                "packageCategory": "Animation/Cartoon",
                "packageKeywords": "Stuart,Sticker",
                "packageAnimated": "N",
                "isNew": "N",
                "artistName": "MightyCat",
                "language": "English",
                "isDownload": "Y"                              //구매 여부
            }
          ]
      }
    }
    ```
 
* **Error Response:**

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist apikey",
      "code": "9000"
    }
    ```
    OR

  * **Code:** 500 Internal Server error <br />
    **Content:** 
    ```json
    {
       "status" : "fail", 
       "message": "server error", 
       "code":"1000"
    }
    ```

* **Sample Call:**

  ```curl
  curl --location --request GET "https://bapi.stipop.io/store/v0.1/download/9937" \ --header "apikey:xxxxxxxxx"
  ```  
  
## 3 Analytics
### 3.1 Sticker Send Analytics 스티커 전송 통계

앱 내에서 사용자가 사용하는 스티커를 데이터화 하는 것은 매우 중요합니다. 앞으로 사용자에게 보다 개인화된 콘텐츠를 제안하고 스토어 성능을 높일 수 있기 때문입니다. 스티팝은 사용자가 전송한 데이터를 통해 이 기능들을 대시보드에 제공합니다. 

* **URL**

  /v0.1/store/analytics/send/:stickerId

* **Method:**

  `POST`
  
*  **Request Headers**

   **Required:**
 
   `apikey=[string]` Issued apikey value

* **Request Path Parameters**

  **Required:**
  
  `stickerId=[int]` 스티커 아이디 값

* **Request Query Parameters**

  **Required:**
  
  `userId=[string]` 각 개별 사용자를 구분 할 수 있는 고유 값


* **Success Response:**

  * **Code:** 200 <br />
    **Content:** <br />
    ```json
    {
      "header": {
          "code": "0000",
          "status": "success",
          "message": "요청 성공"
      },
      "body": []
    }
    ```
 
* **Error Response:**

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist apikey",
      "code": "9000"
    }
    ```
    OR

  * **Code:** 500 Internal Server error <br />
    **Content:** 
    ```json
    {
       "status" : "fail", 
       "message": "server error", 
       "code":"1000"
    }
    ```
    

* **Sample Call:**

  ```curl
  curl --location --request POST "https://bapi.stipop.io/store/v0.1/analytics/send/790?userId=9937" \ --header "apikey:xxxxxxxxx"
  ```



## 4 Common
### 4.1 Category 조회

모든 스티커는 카테고리에 정리되어 있습니다. 카테고리별로 스티커를 리스트하여 사용자에게 보여주면 스토어의 성능이 높아질 수 있습니다. 카테고리 API를 통해 보다 다양하고 효과적인 스토어를 만들어보세요.

* **URL**

  /v0.1/store/category

* **Method:**

  `GET`
  
*  **Request Headers**

   **Required:**
 
   `apikey=[string]` Issued apikey value



* **Success Response:**

  * **Code:** 200 <br />
    **Content:** <br />
    ```json
    {
	    "header": {
		"code": "0000",
		"status": "success",
		"message": "요청 성공"
	    },
	    "body": {
		"categoryList": [
		    {
			"category": "Animation/Cartoon"
		    },
		    {
			"category": "Animals"
		    }
		    ......
		]
	    }
	}
    ```
 
* **Error Response:**

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist apikey",
      "code": "9000"
    }
    ```
    OR

  * **Code:** 500 Internal Server error <br />
    **Content:** 
    ```json
    {
       "status" : "fail", 
       "message": "server error", 
       "code":"1000"
    }
    ```
    

* **Sample Call:**

  ```curl
  curl --location --request GET "https://bapi.stipop.io/store/v0.1/category" \ --header "apikey:xxxxxxxxx"
  ```


## Announcements :loudspeaker:
[Annoucements](https://github.com/stipop-development/Sticker_Store_API/wiki/Announcements)를 통해 최신 업데이트 내용을 확인할 수 있습니다.

## Opening Issues :warning:

> 해당 Github Repository에 Bug 혹은 새로운 Feature 제안 Issue를 생성하실 수 있습니다.
> 기타 문의사항은 <biz@stipop.io>에 연락 부탁드립니다.

- [**bug issue**](https://github.com/stipop-development/Sticker_Store_API/issues/new?template=bug_report.md) 생성하기
- [**feature request**](https://github.com/stipop-development/Sticker_Store_API/issues/new?assignees=&labels=&template=feature_request.md) 생성하기


## License

Stipop Sticker Store API is MIT licensed, as found in the [`LICENSE`](https://github.com/stipop-development/Sticker_Store_API/blob/master/LICENSE) file.
