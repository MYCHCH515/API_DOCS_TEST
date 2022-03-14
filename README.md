# 대기질 정보 조회

> 대기질 정보 조회 api

<h3> Request </h3>

```HTTP
GET /v1/api/air-quality
Host: localhost:8080
```

Parameter 

|Name           |Type            |Description                  |Require        |
| ------------- | -------------- | --------------------------  | :-----------: |
| sidoNm        | String         | 시/구 구분                  | O             |
| guDongNm      | String         | 구/동 구분                  | O             |   


<h3> Response </h3>

|Name           |Type            |Description                   |Require        |
| ------------- | -------------- | --------------------------   |:-------------:|
| siAvg         | Integer        | 시 전체 평균 미세먼지(㎍/㎥)  | O             |
| PM25          | Float          | 초미세먼지농도(㎍/㎥)         | O             |
| PM25Grade     | String         | 초미세먼지농도 등급           | O             |
| PM10          | Float          | 미세먼지(㎍/㎥)               | O             |
| PM10Grade     | String         | 미세먼지 등급                 | O             |
| O3            | Float          | 오존(ppm)                     | O             |   
| O3Grade       | String         | 오존 등급                     | O             |
| NO2           | Float          | 이산화질소 농도(ppm)          | O             |
| NO2Grade      | String         | 이산화질소 농도 등급          | O             |
| CO            | Float          | 일산화탄소 농도(ppm)          | O             |
| NO2Grade      | String         | 일산화탄소 농도 등급          | O             |
| SO2           | Float          | 아황산가스 농도(ppm)          | O             | 
| NO2Grade      | String         | 아황산가스 농도 등급          | O             |



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
