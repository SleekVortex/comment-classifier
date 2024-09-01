
# Фильтрация комментариев

Фильтрация нежелательных комментариев, таких как спам и оскорбления, для создания более качественного анализа мнений людей о ВУЗах.


## Мотивация

Задача проекта состояла в анализе мнений и настроений людей о ВУЗах России в виде отзывов с различных платформ (Отзовик и подобные).

Такая работа проводится несколько лет, в связи с этим накопились данные, благодаря которым можно обучить модели фильтрации нерелевантных отзывов (т.е. не имеющие мнения, являющиеся просто спамом, рекламой, флудом и др.) для того, чтобы качественнее оценить настоящие мнения людей.
## Описание датасета

Датасет - это размеченные отзывы людей о ВУЗах, на основе релевантности мнения, то есть наличия реального мнения о каком-либо ВУЗе, остутсвие спама, рекламы и других ненесущих мнение отзывов.
Поля датасета (text, relevant). text - это текст отзыва, relevant - это 1 или 0, где 1 - это релевантный отзыв.

## Классические методы

Поскольку задача сводится к простой задачае классификации, попробуем применить классические методы классификации текстов (файл classic_methods.ipynb). Лучшее качество которого удалось добиться - это F1 = 0.842.
## Кастомные нейросети

Использовались кастомные простые нейросети (файл nn_methods.ipynb).
В итоге лучше всего себя показали простые нейросети. Лучшее качество модели, которого удалось добиться - это F1 = 0.836, при этом модель обучалась значительно быстрее чем классические.
## Предобученные нейросети

Стандартный и эффективный подход при решении таких задач - это использование Предобученных нейросетей. Например из Hugging Face. 
Хорошим решением будет применить модели на основе Bert, например [cointegrated/rubert-tiny2](https://huggingface.co/cointegrated/rubert-tiny2), она довольно популярна на Hugging Face.
В ходе работы был сделан fine-tuning модели, модель обучилась достаточно быстро и был получен F1 = 0.859. Это оказалось лучшим результатом среди всех моделей, что неудивительно. Это неплохая модель для быстрого решения нашей задачи.
## Результат

Лучшей моделью оказалась модель зафайтюненая на основе cointegrated/rubert-tiny2. Recall у такой модели выше precision, что отлично подходит для нашей задачи фильтрации релевантных текстов, которые в дальнейшем также будут обработаны и изучены.

Полученный результат - это быстрое решение нашей задачи.
## Автор

- [Андрей Заводов (SleekVortex)](https://github.com/SleekVortex)

