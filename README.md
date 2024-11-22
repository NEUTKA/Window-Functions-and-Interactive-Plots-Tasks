# Урок 6: Оконные функции и интерактивные графики

## Описание

Этот урок направлен на изучение динамики цен на авокадо и анализа данных об опозданиях в заключении сделок с использованием оконных функций и интерактивных визуализаций. Мы рассмотрим, как применять скользящие и экспоненциальные средние, а также научимся работать с временными интервалами в данных.

## Описание данных

Данные содержат информацию о ценах и объемах продаж авокадо в США, предоставленные Hass Avocado Board, а также данные об опозданиях при заключении сделок.

### Данные об авокадо
- **Date**: Дата наблюдения
- **AveragePrice**: Средняя цена одного авокадо
- **Total Volume**: Общее количество проданных авокадо
- **4046**: Количество проданных авокадо PLU 4046
- **4225**: Количество проданных авокадо PLU 4225
- **4770**: Количество проданных авокадо PLU 4770
- **Total Bags**: Общее количество упаковок
- **Small Bags**: Количество маленьких упаковок
- **Large Bags**: Количество больших упаковок
- **XLarge Bags**: Количество очень больших упаковок
- **type**: Тип авокадо (обычный или органический)
- **year**: Год наблюдения
- **Region**: Город или регион

### Данные по сделкам
- **client_id**: Идентификатор клиента
- **company_id**: Идентификатор компании
- **delay**: Задержка заключения сделки (в днях)
- **revenue**: Выручка от сделки

## Задачи

1. **Скользящее среднее**  
   Рассчитайте скользящее среднее цены авокадо (`AveragePrice`) с окном, равным 3. Найдите максимальное значение и округлите результат до двух знаков после запятой.

2. **Анализ зависимости скользящего среднего от размера окна**  
   Постройте графики скользящего среднего для значений окна 2, 4, 10, 50. Оцените влияние размера окна на график и соотнесите его с изображениями.

3. **Изучение документации**  
   Ознакомьтесь с параметрами функции в документации и соотнесите их с описанием.

4. **Экспоненциальное скользящее среднее**  
   Примените функцию `ewm()` с параметром `span=2` к средним ценам на авокадо и запишите результат в `avocado_ewm`.

5. **Анализ данных для органического авокадо в Чикаго**  
   Импортируйте данные, указав `index_col=0`. Для органического авокадо (`type='organic'`) в Чикаго (`region='Chicago'`) рассчитайте скользящее среднее с окном 4 и экспоненциальное скользящее среднее с параметром `span=4`. Постройте графики и округлите результаты до трех знаков после запятой.

6. **Преобразование данных по опозданиям в сделках**  
   Прочитайте данные по сделкам и переведите `delay` в формат `timedelta`, убрав знак `-`.

7. **Категоризация времени задержек**  
   Разделите колонку с задержками на 3 интервала и поместите значения в новую колонку `delay_categorical`.

8. **Перезадание категорий задержек**  
   Используя `pd.cut`, присвойте категории следующие значения:
   - `'less than 1 day'` для задержек от 0 до 1 дня
   - `'1-2 days'` для задержек от 1 до 2 дней
   - `'2-3 days'` для задержек от 2 до 3 дней
   - `'more than 3 days'` для задержек свыше 3 дней

9. **Интерактивный график частоты задержек**  
   Постройте интерактивный барплот, отражающий частоту задержек в заключении сделок, отсортировав категории по частоте от самой редкой (внизу) к самой частой (вверху).

---

Этот урок включает практическую работу с оконными функциями и визуализациями, что позволяет углубить понимание временных данных и их применения в анализе.

# Lesson 6: Window Functions and Interactive Charts

## Overview

This lesson focuses on studying avocado price trends and analyzing deal delays using window functions and interactive visualizations. It covers techniques for applying moving averages, exponential averages, and working with time intervals in data.

## Data Description

The data includes information about avocado prices and sales volumes in the U.S., provided by the Hass Avocado Board, as well as deal delay data.

### Avocado Data
- **Date**: Observation date
- **AveragePrice**: Average price of one avocado
- **Total Volume**: Total number of avocados sold
- **4046**: Number of avocados sold with PLU 4046
- **4225**: Number of avocados sold with PLU 4225
- **4770**: Number of avocados sold with PLU 4770
- **Total Bags**: Total number of bags
- **Small Bags**: Number of small bags
- **Large Bags**: Number of large bags
- **XLarge Bags**: Number of extra-large bags
- **type**: Avocado type (conventional or organic)
- **year**: Year of observation
- **Region**: City or region

### Deal Data
- **client_id**: Client ID
- **company_id**: Company ID
- **delay**: Deal delay (in days)
- **revenue**: Revenue from the deal

## Tasks

1. **Moving Average**  
   Calculate the moving average of avocado prices (`AveragePrice`) with a window size of 3. Find the maximum value and round the result to two decimal places.

2. **Effect of Window Size on Moving Average**  
   Plot moving averages with window sizes of 2, 4, 10, and 50. Evaluate the impact of window size on the chart and compare it to the images provided.

3. **Exploring Documentation**  
   Review the parameters of the function in the documentation and relate them to the descriptions provided.

4. **Exponential Moving Average**  
   Apply the `ewm()` function with `span=2` to the avocado price data and save the result as `avocado_ewm`.

5. **Analysis of Organic Avocados in Chicago**  
   Import the data with `index_col=0`. For organic avocados (`type='organic'`) in Chicago (`region='Chicago'`), calculate the moving average with a window size of 4 and the exponential moving average with `span=4`. Plot the results and round the values to three decimal places.

6. **Converting Deal Delay Data**  
   Load the deal data and convert the `delay` column to `timedelta`, removing the `-` sign.

7. **Categorizing Delay Times**  
   Divide the delay column into 3 intervals and store the values in a new column, `delay_categorical`.

8. **Reassigning Delay Categories**  
   Using `pd.cut`, assign the following categories:
   - `'less than 1 day'` for delays from 0 to 1 day
   - `'1-2 days'` for delays from 1 to 2 days
   - `'2-3 days'` for delays from 2 to 3 days
   - `'more than 3 days'` for delays longer than 3 days

9. **Interactive Chart of Delay Frequency**  
   Create an interactive bar plot showing the frequency of deal delays, sorted from the least frequent category (at the bottom) to the most frequent (at the top).

---

This lesson combines practical work with window functions and visualizations, providing a deeper understanding of time-series data and its applications in analysis.

