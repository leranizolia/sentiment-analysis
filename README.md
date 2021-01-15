# sentiment-analysis


Briefing
The task is to predict whether the reviews of goods are positive or negative. 

Evaluation
Submissions are evaluated on area under the ROC curve between the predicted probability and the observed target.

Submission File
For each id in the test set, you must predict a probability for the target variable. The file should contain a header and have the following format:

Id,Probability
1,0.003
2,0.001
3,0.000
etc.

Описание данных:

x_train.txt, x_test.txt – plain text reviews separated by \n.
y_train.csv – target, 1 for positive review and 0 for negative.
random_prediction.csv – a sample submission file in the required format (target is uniformly sampled).


Для скачивания данных: kaggle competitions download -c iad-deep-learning-sentiment

Модель и особенности:

Первоначально была сделана предобработка данных: удаление пунктуации, приведение к нижнему регистру. В качестве эмбеддингов были использованы предобученные эмбеддинги из модели GloVe. Архитектура нейронной сети несложная: всего лишь 2 Bidirectional слоя и 1 Dropout. При этом качество очень высокое: 0.9881.

Проблемой решения этой задачи сначала стала проблема памяти. С помощью более пристального изучения данных было замечено, что основная суть каждого review идёт до ':' - информация до двоеточия в review как будто бы главная мысль отзыва. Поэтому было принято решение обрезать каждый review до ':'. Такая проблема была на kaggle-kernel и, соответственно, когда данные существенно уменьшились, она исчезла. На google colab проблемы с RAM не было, поэтому можно было не обрезать данные, а обучить модель на полном датасете. Именно поэтому в репозитории можно найти 2 ноутбука: с обрезанным датасетом и без. 
