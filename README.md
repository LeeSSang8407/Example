# Example

from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome("chromedriver")
driver.get("https://www.naver.com")

# Naver 메인에서 웹툰 항목을 클릭하도록 지정 
# 크롬에서 F12를 클릭 후 개발자 도구 클릭
# 좌측상단 Inspector 아이콘 클릭해서 대상개소 확인 후 우측버튼 + 복사 (copy selector)
# 예시 : NM_FAVORITE > div.group_nav > ul.list_nav.NM_FAVORITE_LIST > li:nth-child(8) > a

# Chrome 제어측에서 '웹툰'을 찾아서 자동으로 클릭 
# driver.find_element(By.CSS_SELECTOR, "#NM_FAVORITE > div.group_nav > ul.list_nav.NM_FAVORITE_LIST > li:nth-child(8) > a").click()

# 네이버 사전 클릭 → 검색창에 교육 입력 → 검색결과를 표시
driver.find_element(By.CSS_SELECTOR, "#NM_FAVORITE > div.group_nav > ul.list_nav.NM_FAVORITE_LIST > li:nth-child(1) > a").click()
driver.find_element(By.CSS_SELECTOR, "#ac_input").send_keys("교육")
driver.find_element(By.CSS_SELECTOR, "#dicSearch > a").click()
meaning_sel = "#content > div.kr_dic_section.search_result.dic_kr_entry > ul > li:nth-child(1) > p:nth-child(2)"
education = driver.find_element(By.CSS_SELECTOR, meaning_sel)
education.text()
