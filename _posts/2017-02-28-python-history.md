---
layout: post
title: Python 
tags: history python
---

## Кто?
Гвидо ван Россум

## Что?
Python. Автор назвал язык в честь популярного британского комедийного телешоу 1970-х «Летающий цирк Монти Пайтона». 

Расширения файлов: .py

## Дзен (философия) Python
- Красивое лучше, чем уродливое.
- Явное лучше, чем неявное.
- Простое лучше, чем сложное.
- Сложное лучше, чем запутанное.
- Плоское лучше, чем вложенное.
- Разреженное лучше, чем плотное.
- Читаемость имеет значение.
- Особые случаи не настолько особые, чтобы нарушать правила.
- При этом практичность важнее безупречности.
- Ошибки никогда не должны замалчиваться.
- Если не замалчиваются явно.
- Встретив двусмысленность, отбрось искушение угадать.
- Должен существовать один — и, желательно, только один — очевидный способ сделать это.
- Хотя он поначалу может быть и не очевиден, если вы не голландец.
- Сейчас лучше, чем никогда.
- Хотя никогда зачастую лучше, чем прямо сейчас.
- Если реализацию сложно объяснить — идея плоха.
- Если реализацию легко объяснить — идея, возможно, хороша.
- Пространства имён — отличная штука! Будем делать их побольше!

Разработчики языка Python придерживаются определённой философии программирования, 
называемой «The Zen of Python». Её текст выдаётся интерпретатором Python по команде import this 
(работает один раз за сессию). 

Автором этой философии считается Тим Петерс (Tim Peters).

## Когда?
1991г.

## Какой?
Мультипарадигмальный, объектно-ориентированный...

Динамический: позволяет определять типы данных и осуществлять синтаксический анализ и компиляцию «на лету», 
на этапе выполнения программы. Динамические языки удобны для быстрой разработки приложений.

Функциональный: Python поддерживает парадигму функционального программирования.

## Сколько?
Два основных выпуска, которые развиваются параллельно: Python 2.x и Python 3.x.
Python 3.0 обратно не совместим с предыдущей серией 2.x. 
Код Python 2.x часто будет выдавать ошибки при исполнении в Python 3.0. 

## Пример кода (Анаграммы)

```python
# coding: utf-8
import random


def input(propmt):
    return raw_input(propmt).decode('cp1251')


def play():
    words = read_words(open('dict.txt', 'r'))
    score = [0, 0]
    show_rules()
    while True:
        answer = input(u'Продолжить? (да/нет) ')
        if answer == u'нет':
            print u'Счёт: ', score
            print u'Пока!'
            return
        elif answer == u'да':
            anagram = make_anagram(words)
            print repr(anagram)
            answer = input(u'Какое это слово - "' + anagram + u'"? ')
            ok = check_answer(anagram, answer, words)
            change_score(ok, score)
            if ok:
                print u'Верно!'
            else:
                print u'Неверно!'
            print u'Счёт: ', score


def show_rules():
    print u'''В данной игре Вам даётся слово с перемешанными буквами, анаграмма.
Ваша цель: угадать слово, задуманное в игре (решить анаграмму).'''


def make_anagram(words):
    word = words[random.randint(0, len(words)-1)]
    anagram = word
    while anagram == word:
        anagram = anagrams(word)
    return anagram


def anagrams(word):
    word = list(word)
    anagram = []
    while len(word) > 0:
        i = random.choice(word)
        word.remove(i)
        anagram.append(i)
    return ''.join(anagram)


def change_score(ok, score):
    score[1] += 1
    if ok:
        score[0] += 1


def check_answer(anagram, answer, words):
    if answer in words and check(anagram, answer):
        return True


def check(anagram, answer):
    anagram = list(anagram)
    answer = list(answer)
    if len(anagram) == len(answer):
        for e in answer:       
            if e in anagram:
                anagram.remove(e)
        if len(anagram) == 0:
                return True
    

def read_words(file):
    words = []
    for line in file:
        words.append(line.decode('utf-8').rstrip('\n'))
    return words


if __name__ == '__main__':
    play()
```

## Интересно
- [Пишем красивый идиоматический Python](https://habrahabr.ru/post/204476/)