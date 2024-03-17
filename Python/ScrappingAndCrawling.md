# Scrapping & Crawling
* 스크래핑과 크롤링을 위해 필요한 데이터를 웹페이지에서 받아오기 위해서는 request 모듈이 필요하다
    * `import request`

## Web Scrapping

* 웹 스크래핑 : 특정 웹사이트에서 데이터를 추출하는 방법, 웹 사이트의 특정 데이터 집합에 초점을 맞추며 추출한 데이터를 CSV, XML, JSON 등으로 변환

* BeautifulSoup : 파이썬 스크래핑 패키지
    * `from bs4 import BeautifulSoup`

* Code : 할리스 커피에서 커피메뉴 받아와서 csv파일로 만들기

```python
    import request
    import pandas as pd
    from bs4 import BeautifulSoup

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

    coffee = []

    for index, element in enumerate(data_list, 1):
        # 리스트 범위를 초과 하므로 -1
        print(data_list[index-1].text)
        coffee.append(element.text)
    
    # pandas의 Dataframe에 데이터 담기
    df = pd.DataFrame()
    df['coffee'] = coffee

    # csv 파일 생성
    df.to_csv('./hollys_.csv')

```

## Web Crawling 

* 웹 크롤링 : 웹 사이트의 모든 페이지를 방분하여 콘텐츠를 색인화하고 저장한다

* webdriver : 
    * `from selenium import webdriver`

* Code : 부산에 있는 할리스 커피 지점 정보 받아오기

```python
    from bs4 import BeautifulSoup
    import pandas as pd
    from selenium.webdriver.common.by import By
    from selenium.webdriver.common.keys import Keys
    from selenium import webdriver
    import time

    driver = webdriver.Chrome()

    url = 'https://www.hollys.co.kr/store/korea/korStore2.do'

    driver.get(url)

    # 부산 데이터를 찾기 위해 검색창에 부산 검색
    search_input = driver.find_element(By.ID, 'store')
    search_input.send_keys('부산')
    time.sleep(0.5)
    search_input.send_keys(Keys.ENTER)
    time.sleep(0.5)

    # 응답받은 HTML 을 BeautifulSoup 클래스의 객체 형태로 생성 및 반환
    html = driver.page_source
    soup = BeautifulSoup(html, 'html.parser')

    # tb_store 클래스인 table 아래 tbody > tr > td
    store_name = soup.select('table.tb_store > tbody > tr > td')

    store_info = []

    for index in store_name:
        print(index.text.strip())ㄴ
        store_info.append(index.text)

    df = pd.DataFrame()
    df['store_name'] = store_info

    df.to_csv('./hollys_info.csv')
    
```

## 참조

* https://library.gabia.com/contents/9239/

* https://beomi.github.io/2017/02/27/HowToMakeWebCrawler-With-Selenium/