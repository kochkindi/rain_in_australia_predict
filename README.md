# Predict rain in Australia
- В данной работе была предпринята попытка предсказать возможность дождя на следующий день на основе данных гидрометцентра за 10 лет в Австралии. Была поставлена задача классификации.

https://www.kaggle.com/datasets/jsphyg/weather-dataset-rattle-package

- В качестве признаков было представлено несколько полей, обзор, анализ, визуализация и обработка которых представлена в разделе "Обзор данных и признаков".

- Отдельный и один из самых важных (и скорее всего спорных) разделов - "Обработка пропущенных значений" также представлен в работе. Была проведена замена пропущенных значений различными способами, исходя из результатов распределений и типа данных (дискретных, непрерывных и тд величин).

1.

- В качестве бейзлайна на основе оригинальных данных с обработанными пропущенными значениями была представлена модель Логистической Регрессии, результаты которой на тестовой выборке:
Accuracy: 0.82084
Precision: 0.6562
Recall: 0.3808
ROC_AUC: 0.8184

- После этого были созданы новые колонки в разделе "Создание и преобразование новых признаков", соответственно, результат улучшился на предыдущей модели и достиг показателей:
Accuracy: 0.8433
Precision: 0.7215
Recall: 0.4763
ROC_AUC: 0.8582

- Для улучшения показателей была проведена балансировка классов целевой переменной методом undersampling, после чего результат улучшился до показателей:
Accuracy: 0.7717
Precision: 0.7855
Recall: 0.7502
ROC_AUC: 0.8577
Можно заметить, что результат по Recall сильно улучшился как раз благодаря балансировке классов.

- В качестве дальнейшей попытки улучшения модели Логистической Регрессии также было опробовано масштабирование данных методов MinMax. Результат изменился до показателей:
Accuracy: 0.7871
Precision: 0.7980
Recall: 0.7726
ROC_AUC: 0.8703

2.

- В качестве альтернативы была опробована модель RandomForest, на несбалансированных классах целевой переменной результат получился:
Accuracy: 0.8539
Precision: 0.7756
Recall: 0.4912
ROC_AUC: 0.8837

- На сбалансированных классах и на подобранных гиперпараметрах с помощью CVGridSearch RandomForest показал:
Accuracy: 0.7789
Precision: 0.7854
Recall: 0.7661
ROC_AUC: 0.8630
Поиск проходил по гиперпараметрам n_estimators, max_depth, max_features, criterion.

3.

- Использование GradientBoosting из библиотеки sklearn:
Accuracy: 0.7853
Precision: 0.7887
Recall: 0.7779
ROC_AUC: 0.8705
Так как результат улучшился, то была предпринята попытка продолжить тему с градиентным бустингом:

- XGBoost без подбора гиперпараметров:
Accuracy: 0.8028
Precision: 0.8018
Recall: 0.7984
ROC_AUC: 0.8862

- XGBoost с подбором гиперпараметров при помощи CVGridSearch:
Accuracy: 0.8058
Precision: 0.8094
Recall: 0.7972
ROC_AUC: 0.8897
Поиск проходил по гиперпараметрам: learning_rate, gamma, max_depth, n_estimators.

Итого: был проведен анализ данных гидрометцентра за 10 лет, а также прогнозирование дождня на следующий день. Лучший результат показала модель XGBoostClassifier. Результат работы:

Accuracy: 0.8058
Precision: 0.8094
Recall: 0.7972
ROC_AUC: 0.8897
