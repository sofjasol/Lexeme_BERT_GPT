# Lexeme_BERT_GPT
Посмотрим, как модель справляется с выбором одной из близких о значению испанских лексем в зависимости от контекста. Сначала посмотрим на модель с пропусками, а потом на левостороннюю модель

Можно сказать, что в нашем случае и с нашей задачей и с нашим языком левосторонняя модель показала себя лучше, чем модель с пропусками. Почему?
- она, хоть и не всегда, отдает предпочтение правильному/ожидаемому результату
- она лучше распознает идиомы

Примеры работы модели:
1.
```
texts = [
     "Hace mucho calor.",
     "Tiene mucho calor."
]
compare(texts)
```

```
Hace mucho calor.
Hace:0.000 mucho:0.054 calor:0.022 .:0.215 
Minus log prob: 17.55

Tiene mucho calor.
Tiene:0.000 mucho:0.004 calor:0.006 .:0.214 
Minus log prob: 21.91

```

2.
```
texts = [
     "El problema está sobre la mesa.",
     "El problema está en la mesa."
]
compare(texts)
```

```
El problema está sobre la mesa.
El:0.006 problema:0.003 estÃ¡:0.013 sobre:0.002 la:0.153 mesa:0.033 .:0.304 
Minus log prob: 27.92

El problema está en la mesa.
El:0.006 problema:0.003 estÃ¡:0.013 en:0.543 la:0.089 mesa:0.000 .:0.210 
Minus log prob: 27.55
```

