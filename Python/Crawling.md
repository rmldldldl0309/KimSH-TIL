# Scrapping & Crawling
* 스크래핑과 크롤링을 위해 필요한 데이터를 웹페이지에서 받아오기 위해서는 request 모듈이 필요하다
    * `import request`

## Web Scrapping

* BeautifulSoup : 파이썬 스크래핑 패키지
    * `from bs4 import BeautifulSoup`

* Code : 할리스 커피에서 커피메뉴 받아오기
```python
    # requests를 이용해 get요청을 보내고 응답받기
    URL = 'https://www.hollys.co.kr/menu/espresso.do'
    response = requests.get(URL)

    # 응답받은 HTML 을 BeautifulSoup 클래스의 객체 형태로 생성 및 반환
    html = response.text
    soup = BeautifulSoup(html, 'html.parser')
    # menu.list01 클래스로 설정된 ul태그 아래의 a태그
    data_list = soup.select(
        'ul.menu_list01 a'
    )
    for index, element in enumerate(data_list, 1):
        print(data_list[index].text)
```

위의 코드를 통해 아래와 같은 결과를 얻을 수 있다

`
    블랙아리아딥라떼
    돌체 라떼
    디카페인아메리카노
    디카페인바닐라 딜라이트
    콜드브루 딜라이트
    콜드브루
    바닐라 딜라이트
    카페모카
    카푸치노
    카페 라떼
    에스프레소
`




## Web Crawling 

* webdriver : 
    * `from selenium import webdriver`