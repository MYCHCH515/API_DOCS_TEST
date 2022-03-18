# 대기질 정보 조회

> 대기질 정보 조회 api

<h3> Request </h3>

```HTTP
GET /v1/api/air-quality/{sidoName}?gu={gu}
Host: localhost:8080
```

Parameter 

|Name           |Type            |Description                                       |Required       |
| ------------- | -------------- | ------------------------------------------------ | :-----------: |
| sidoName      | String         | 시/도 구분 ex) *seoul : 서울시, busan :부산시*    | O             |
| gu            | String         | 구/동 구분 ex) *용산구, 마포구, ...*              | X             |   


<h3> Response </h3>

|Name                |Child            |Type            |Description                                                   |Required       |
| ------------------ | :------------: | -------------- | ------------------------------------------------------------ |:-------------:|
| sido               | -              | String         | 시/도 명                                                     | O             |
| sidoPm10Avg        | -              | Double         | 시 전체 평균 미세먼지 수치 (㎍/㎥)                            | X             |
| sidoPm10AvgGrade   | -              | String         | 시 전체 평균 미세먼지 등급 ex) *좋음 , 보통, 나쁨, 매우나쁨*  | X             |
| guList             | -              | Array          | 자치구 대기질 정보 리스트                                    | X             |
|                    | gu             | String         | 자치구 명 ex) *용산구, 마포구, ...*                          | X             |
|                    | pm25           | Integer        | 초미세먼지 수치 (㎍/㎥)                                      | X             |
|                    | pm25Grade      | String         | 초미세먼지농도 등급 ex) *좋음 , 보통, 나쁨, 매우나쁨*         | X             |
|                    | pm10           | Integer        | 미세먼지 수치 (㎍/㎥)                                        | X             |
|                    | pm10Grade      | String         | 미세먼지 등급 ex) *좋음 , 보통, 나쁨, 매우나쁨*               | X             |
|                    | o3             | Double         | 오존 수치 (ppm)                                              | X             |   
|                    | o3Grade        | String         | 오존 등급 ex) *좋음 , 보통, 나쁨, 매우나쁨*                   | X             |
|                    | no2            | Double         | 이산화질소 수치 (ppm)                                        | X             |
|                    | no2Grade       | String         | 이산화질소 농도 등급 ex) *좋음 , 보통, 나쁨, 매우나쁨*        | X             |
|                    | co             | Double         | 일산화탄소 수치 (ppm)                                        | X             |
|                    | coGrade        | String         | 일산화탄소 농도 등급 ex) *좋음 , 보통, 나쁨, 매우나쁨*        | X             |
|                    | so2            | Double         | 아황산가스 수치 (ppm)                                        | X             | 
|                    | so2Grade       | String         | 아황산가스 농도 등급 ex) *좋음 , 보통, 나쁨, 매우나쁨*        | X             |



<hr>

> Sample

### Request : 서울시 전체 자치구 대기질 정보 조회

```HTTP
GET http://localhost:8080/v1/api/air-quality/seoul
```

### Response

```JSON
HTTP/1.1 200 OK
{  
  "sido": "서울시",
  "sidoPm10Avg": 4,
  "sidoPm10AvgGrade": "좋음",
  "guList": [
      {
       "gu": "중구",
       "pm25": 5,
       "pm25Grade": "좋음",
       "pm10": 10,
       "pm10Grade": "좋음",
       "o3": 0.039,
       "o3Grade": "보통",
       "no2": 0.015,
       "no2Grade": "좋음",
       "co": 0.3,
       "coGrade": "좋음",
       "so2": 0.003,
       "so2Grade": "좋음"  
     },
     {
       "gu": "종로구",
       "pm25": 3,
       "pm25Grade": "보통",
       "pm10": 6,
       "pm10Grade": "보통",
       "o3": 0.037,
       "o3Grade": "좋음",
       "no2": 0.010,
       "no2Grade": "좋음",
       "co": 0.3,
       "coGrade": "좋음",
       "so2": 0.002,
       "so2Grade": "좋음"  
     },
     ...
  ]
}
```

### Request : 자치구별 대기질 정보 조회

```HTTP
GET http://localhost:8080/v1/api/air-quality/seoul?gu=용산구
```

### Response

```JSON
HTTP/1.1 200 OK
"sido": "서울시",
  "sidoPm10Avg": 4,
  "sidoPm10AvgGrade": "좋음",
  "guList": [
      {
       "gu": "중구",
       "pm25": 5,
       "pm25Grade": "좋음",
       "pm10": 10,
       "pm10Grade": "좋음",
       "o3": 0.039,
       "o3Grade": "보통",
       "no2": 0.015,
       "no2Grade": "좋음",
       "co": 0.3,
       "coGrade": "좋음",
       "so2": 0.003,
       "so2Grade": "좋음"  
     },
```
