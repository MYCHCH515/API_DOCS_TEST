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

### Request : 서울시 용산구 

```
curl -v -G GET "http://localhost:8080/v1/api/air-quality" \
     -d "sidoNm=서울시" \
     -d "guDongNm=용산구" \
```

### Response

```JSON
HTTP/1.1 200 OK
{
  "siAvg": 5,
  "PM25": 2.0,
  "PM25Grade": "좋음",
  "PM10": 6.0,
  "PM10Grade": "좋음",
  "O3": 0.039,
  "O3Grade": "좋음",
  "NO2":0.025,
  "NO2Grade": "좋음",
  "CO": 0.4,
  "COGrade": "좋음",
  "SO2":0.002,
  "SO2Grade": "좋음"
}
```
