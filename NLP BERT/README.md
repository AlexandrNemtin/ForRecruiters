## Проект для «Викишоп» с BERT
Интернет-магазин «Викишоп» запускает новый сервис. Теперь пользователи могут редактировать и дополнять описания товаров, как в вики-сообществах. То есть клиенты предлагают свои правки и комментируют изменения других. Магазину нужен инструмент, который будет искать токсичные комментарии и отправлять их на модерацию.

## Задача

Обучить модель классифицировать комментарии на позитивные и негативные. Значение метрики качества F1 на обученной модели не меньше 0.75.

## Описание данных

Данные находятся в файле toxic_comments.csv. Столбец text в нём содержит текст комментария, а toxic — целевой признак.

## Навыки и инструменты

- **python**
- **pandas**
- **numpy**
- **PyTorch**
- transformers.**BertForSequenceClassification**
- transformers.**BertTokenizer**
- transformers.**BertModel**
- sklearn.svm.**SVC**

## Описание хода решения

В процессе решения задачи использовалась предобученная модель с сервича HuggingFace.co - JungleLee. Набор комментариев токенизировали, выровняли размеры векторов при помощи пэддинга и введения маски. 

После подготовки данных обучена модель sklearn.svm.SVC с показателем заявленной метрики f1 равной 0.8776 на валидации. На тестовой выборке - 0.8845, что соотвествовало условию задачи.
Код написан с использованием GPU на Google Colab. 

## Вывод

Была проведена исследовательская работа по обработке текстов и обучению и выбору модели для определения токсичных комментариев по методу работы с BERT. Для обучения выбрана модель обучения методом опорных векторов SVC. 

Дальнейшие работы нужно согласовать с заказчиком. Например, можно улучшить финальный результат работы модели, если это необходимо, проанализировав матрицу ошибок и выделив, с ошибками какого рода нужно бороться больше (и нужно ли).
