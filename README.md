from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.chrome.options import Options
import math
import time

# Укажите путь к исполняемому файлу ChromeDriver
chrome_driver_path = "C:\\chromedriver\\chromedriver.exe"

# Инициализация ChromeOptions
options = Options()
options.add_argument("--start-maximized")  # Максимизировать окно браузера

# Инициализация WebDriver с помощью ChromeDriver
driver_service = Service(chrome_driver_path)
driver = webdriver.Chrome(service=driver_service, options=options)

try:
    # Открыть веб-страницу
    driver.get("https://suninjuly.github.io/execute_script.html")

    # Найти элемент с id "input_value" и считать текст
    x_element = driver.find_element("css selector", "#input_value")
    x = int(x_element.text)

    # Посчитать значение математической функции от x
    result = str(math.log(abs(12*math.sin(x))))

    # Прокрутить страницу вниз, чтобы элементы стали видимыми
    driver.execute_script("window.scrollBy(0, 100);")

    # Ввести результат вычислений в текстовое поле
    answer_input = driver.find_element("css selector", "#answer")
    answer_input.send_keys(result)

    # Выбрать checkbox "I'm the robot"
    checkbox = driver.find_element("css selector", "#robotCheckbox")
    checkbox.click()

    # Выбрать radiobutton "Robots rule!"
    radio = driver.find_element("css selector", "#robotsRule")
    radio.click()

    # Нажать на кнопку "Submit"
    submit_button = driver.find_element("css selector", "button[type='submit']")
    submit_button.click()

    time.sleep(5)  # Пауза для наблюдения результата перед закрытием

finally:
    # Закрыть окно браузера
    driver.quit()
Задание на execute_script
В данной задаче вам нужно будет снова преодолеть капчу для роботов и справиться с ужасным и огромным футером, который дизайнер всё никак не успевает переделать. Вам потребуется написать код, чтобы:

Открыть страницу https://SunInJuly.github.io/execute_script.html.
Считать значение для переменной x.
Посчитать математическую функцию от x.
Проскроллить страницу вниз.
Ввести ответ в текстовое поле.
Выбрать checkbox "I'm the robot".
Переключить radiobutton "Robots rule!".
Нажать на кнопку "Submit".
Если все сделано правильно и достаточно быстро (в этой задаче тоже есть ограничение по времени), вы увидите окно с числом. Отправьте полученное число в качестве ответа для этого задания.

Для этой задачи вам понадобится использовать метод execute_script, чтобы сделать прокрутку в область видимости элементов, перекрытых футером.
