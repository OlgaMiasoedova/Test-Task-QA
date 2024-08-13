# Задача Playwright:

## Условие:

Написать тест, который открывает веб-страницу https://playwright.dev/, проверяет, что она существует, и что заголовок страницы соответствует ожидаемому значению.

## Ожидаемый результат:

Тест, успешно проходящий проверку заголовка.

## Решение:

```ruby        
from playwright.sync_api import Playwright, sync_playwright, expect


def run(playwright: Playwright) -> None:
    browser = playwright.chromium.launch(headless=False)
    context = browser.new_context()
    page = context.new_page()
    page.goto('https://playwright.dev/')
    assert page.title() == "Playwright enables reliable end-to-end testing for modern web apps."
    context.close()
    browser.close()


with sync_playwright() as playwright:
    run(playwright)
```
