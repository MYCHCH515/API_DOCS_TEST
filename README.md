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
| PM10          | Float          | 미세먼지(㎍/㎥)               | O             |
| O3            | Float          | 오존(ppm)                     | O             |   
| NO2           | Float          | 이산화질소농도(ppm)           | O             |
| CO            | Float          | 일산화탄소농도(ppm)           | O             |
| SO2           | Float          | 아황산가스농도(ppm)           | O             |   



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
  "siAvg":5,
  "PM25": 2.0,
  "PM10": 6.0,
  "O3": 0.039,
  "NO2":0.025,
  "CO": 0.4,
  "SO2":0.002
}
```
