# Emergency Message App BackEnd

## Install
1. nodejs
2. express
3. maria db

참고 사이트 : https://www.youdad.kr/making-simple-node-api-server

## Execute
```
$ npm start
```
# API
## Message List
날짜별 재난문자 리스트를 가져온다.


### Request
```
POST /list
```
```
{
    "start":string,
    "end":string,
}
```
example
```
{
    "start":"2023-03-04",
    "end":"2023-03-05",
}
```

### Response
```
{
    "inputDate":[
      {"num":number, "division":string, "step":string, "title":string}
    ]
}
```
example
```
{
    "2023-03-05":[
      {"num":192577, "division":"기타", "step":"안전안내", "title":"2023/03/05 20:04:12 [서울경찰청]", "region": "서울특별시", "area": "강북구"}
    ],
    "2023-03-04":[
      {"num":192576, "division":"전염병", "step":"안전안내", "title":"2023/03/04 20:04:12 [대전경찰청]", "region": "대전광역시", "area": "동구"},
      {"num":192575, "division":"한파", "step":"안전안내", "title":"2023/03/04 20:04:12 [대구경찰청]", "region": "대구광역시", "area": "남구"}
     ],
}
```

## Contents
글 별로 가지고 있는 내용들을 가져온다.

### Request
```
POST /contents
```
```
{
    "num": number
}
```
example
```
{
    "num":192577,
}
```

### Response
```
{"title":string, "region":string, "date":string, "content":string}
```
example
```
{"title":"2023/02/02 20:04:12 [서울경찰청]", "region":"서울 마포구", "date":"2023-02-02 20:04:30", "content":"[북구청] 북구 중산동 갓안마을 인근 일원에 야생 멧돼지가 출몰하였으니 주민들께서는 안전에 유의하여 주시기 바랍니다."}
```
