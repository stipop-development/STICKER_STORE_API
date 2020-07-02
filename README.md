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

> Stipop provides a powerful and flexible sticker API that enables companies to add stickers onto their apps and websites with minimum effort and maximum effect.

Stickers are one of the most powerful visual contents you can find in the digital world. With more than 50 billion being sent everyday, and unlike GIFs, it brings emotion into online communicaton, because a specific artist created it with a purpose (for online communication, character etc.) this makes stickers very unique and usable and tailored to all tastes. 

Seeing how sticker are a useful kind of media, we as a team started a platform, where stickers and sticker lovers can play about. Our product began as an app for messenger users to download stickers for their personal use. Now that there is more than 5,000 sticker artists participating from 15 different countries and the total stickers accumulate to 100,000 we thought it would be best that other companies should also be able to provide stickers to their own users.


## Key Features
* Sticker Package
  - 100,000 stickers uploaded by 5,000 global artists around the world. 
  - Customized sticker packs that capture the preferences of your target users, recommended and assorted through Stipop’s millions of user data. 
* Multi-language Contents
  - English/Spanish/Hindi/Russian/German/French/Portuguese/Italian/Simplified-Chinese/Traditional-Chinese/Catonese/Japanese/Thai/Indonesian
/Korean
* Regional Best
  - Top 100 download list provided in specified langauge speaking countries
* Daily Update
  - All sticker list updated in a daily basis with new stickers added in automatically
* Favorites (preparing)
  - API to provide list of stickers used the most by a specific end user


## Get started :rocket:

To get started, review sections below in the 'README' files in the [Stipop_Sticker_Store API](https://github.com/stipop-development/STICKER_STORE_API/blob/master/README.md) repository.




# Endpoints

## 1. Package

### 1.1 Package Ranking List 스티커팩 인기순위 조회

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
  
### 2.2 Download History 구매내역 조회

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
Please check out [Annoucements](https://github.com/stipop-development/Stipop_Sticker_API/wiki/Announcements) for recent changes.

## Opening Issues :warning:

> Only use the GitHub Issues section if you discovered **issues with the code itself**. Do not mistake the Issues page as a help desk. You can ask for help at [Stack Overflow](https://stackoverflow.com/).  
> For support, please contact <webmaster@stipop.io>.

- Create a [**general issue**](https://github.com/stipop-development/Stipop_Sticker_API/issues/new?template=general.md)


## License

Stipop Sticker API is MIT licensed, as found in the [`LICENSE`](https://github.com/stipop-development/Stipop_Sticker_API/blob/master/LICENSE) file.
