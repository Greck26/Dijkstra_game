# Dijkstra_game
from random import randint as rand
import os
import turtle
import time

#Дейкстра по матрице смежности.
def Dijkstra(N, S, matrix):
    valid = [True]*N        
    weight = [1000000]*N
    weight[S] = 0
    path = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
    for i in range(N):
        min_weight = 1000001
        ID_min_weight = -1
        for i in range(len(weight)):
            if valid[i] and weight[i] < min_weight:
                min_weight = weight[i]
                ID_min_weight = i
        for i in range(N):
            if weight[ID_min_weight] + matrix[ID_min_weight][i] < weight[i]:
                weight[i] = weight[ID_min_weight] + matrix[ID_min_weight][i]
                path[i] = ID_min_weight+1
        valid[ID_min_weight] = False
    return path, weight

#Игра вопрос-ответ.
def question(n):
    print('ВНИМАНИЕ Вопрос!')
    print()
    q_f = open("questions.txt")
    s_q = ''
    
    # Цикл считывает нужную нам строку из файла.
    for i, line in enumerate(q_f):
        if i == (n-1):
            s_q = line
            
    print(s_q)
    f = False
    a_f = open("answers.txt")
    s_a = ''
    
    for i, line in enumerate(a_f):
        if i == (n-1):
            s_a = line
            
    print('Ваш ответ:')
    ans = input()
    ans += '\n'
    if ans == s_a:
        f = True
        print("ПРАВИЛЬНО! УРА! Едем дальше!")
    else:
        print('Неверено! К сожалению вы проиграли. Попробуйте снова')
        print()
        print('Нажмите ENTER для выхода из программы')
        
    input()
    q_f.close()
    a_f.close()
    return f

# Блоки рисовалок
def seven():
    turtle.goto(-200, 60)
    turtle.color('red')
    turtle.write(7)
    turtle.color("blue") # Устанавливаем цвет черепашки
    turtle.circle(15) # Рисуем круг с радиусом 45    
    turtle.color("black")

def five():
    turtle.goto(0, 0)
    turtle.color('red')
    turtle.write(5)
    turtle.color("blue")
    turtle.circle(15)    
    turtle.color("black")

def six():
    turtle.goto(-200, -60)
    turtle.color('red')
    turtle.write(6)
    turtle.color("blue")
    turtle.circle(15)
    turtle.color("black")
    
def four():
    turtle.goto(-100, -60)
    turtle.color('red')
    turtle.write(4)
    turtle.color("blue")
    turtle.circle(15)
    turtle.color("black")

def one():
    turtle.goto(100, -90)
    turtle.color('red')
    turtle.write(1)
    turtle.color("blue")
    turtle.circle(15)
    turtle.color("black")

def two():
    turtle.goto(100, -40)
    turtle.color('red')
    turtle.write(2)
    turtle.color("blue")
    turtle.circle(15)
    turtle.color("black")

def three():
    turtle.goto(40, -40)
    turtle.color('red')
    turtle.write(3)
    turtle.color("blue")
    turtle.circle(15)
    turtle.color("black")

def eight():
    turtle.goto(0, 100)
    turtle.color('red')
    turtle.write(8)
    turtle.color("blue")
    turtle.circle(15)
    turtle.color("black")

def nine():
    turtle.goto(100, 100)
    turtle.color('red')
    turtle.write(9)
    turtle.color("blue")
    turtle.circle(15)
    turtle.color("black")

def ten():
    turtle.goto(100, 20)
    turtle.color('red')
    turtle.write(10)
    turtle.color("blue")
    turtle.circle(15)

def four_five():
    turtle.goto(0,0)
    turtle.pendown()
    turtle.goto(-100, -60)

def three_nine():
    turtle.goto(40, -40)
    turtle.pendown()
    turtle.goto(100, 100)

def three_five():
    turtle.goto(0, 0)
    
# Отрисовка значений масс ребер
def draw_line_time():
    turtle.penup()
    turtle.color('green')
    turtle.goto(-100, 30)
    turtle.write(18)
    turtle.goto(-100, -30)
    turtle.write(15)
    turtle.goto(-150, -60)
    turtle.write(3)
    turtle.goto(-50, -43)
    turtle.write(7)
    turtle.goto(5, -90)
    turtle.write(10)
    turtle.goto(105, -60)
    turtle.write(3)
    turtle.goto(65, -40)
    turtle.write(4)
    turtle.goto(20, -20)
    turtle.write(3)
    turtle.goto(5, 50)
    turtle.write(6)
    turtle.goto(50, 105)
    turtle.write(17)
    turtle.goto(105, 55)
    turtle.write(12)
    turtle.goto(50, 20)
    turtle.write(20)
    
#Основное тело программы.
class main():
    
    INF = 1000000

    turtle.penup() # Поднимаем курсор
    turtle.goto(-200, 50) # Переходим по нужным координатам
    turtle.pendown() # Опускаем курсор
    
    # Отрисовка графа
    seven()
    five()
    six()
    four()
    one()
    two()
    three()
    three_five()
    eight()
    nine()
    ten()
    turtle.color('black')
    turtle.penup()
    four_five()
    turtle.penup()
    three_nine()
    draw_line_time()
    #Координаты вершин графа в рисовалке
    coordinats = [[100, -90], [100, -40], [40, -40], [-100, -60], [0, 0], [-200, -60], [-200, 60], [0, 100], [100, 100], [100, 20]]

    #Матрица смежности графа дорог.
    matrx = [[INF, 3, INF, 10, INF, INF, INF, INF, INF, INF], [3, INF, 4, INF, INF, INF, INF, INF, INF, INF],
             [INF, 4, INF, INF, 3, INF, INF, INF, 20, INF], [10, INF, INF, INF, 7, 3, INF, INF, INF, INF],
             [INF, INF, 3, 7, INF, 15, 18, 6, INF, INF], [INF, INF, INF, 3, 15, INF, INF, INF, INF, INF],
             [INF, INF, INF, INF, 18, INF, INF, INF, INF, INF], [INF, INF, INF, INF, 6, INF, INF, INF, 17, INF],
             [INF, INF, 20, INF, INF, INF, INF, 17, INF, 12], [INF, INF, INF, INF, INF, INF, INF, INF, 12, INF]]
    
    print("""
          




          
          ЗДРАВСТВУЙТЕ! ДОБРО ПОЖАЛОВАТЬ В ИГРУ!



                                                                """)
    input()
    print()
    print("Внимание! Все ответы вводятся строчными буквами")
    print()
    print('Введите отправную точку (число от 1 до 10)')
    N = int(input())
    os.system('cls')
    print('Итак мы начинаем с точки № ', N)
    turtle.penup()
    turtle.color('red')
    turtle.goto(coordinats[N-1][0], coordinats[N-1][1])
    input()
    counter = 1
    now_point = N
    visited = set()
    
    # Основной цикл.
    while counter <= 11:
        if not(now_point in visited):
            if (question(now_point) == False):
                exit()
            visited.add(now_point)
            os.system('cls')
            pre_point = now_point
            if len(visited) == 10:
                break
            while (now_point in visited):
                now_point = rand(1, 10)
            print('Итак, следущая точка № ', now_point)
            min_path, min_weight = Dijkstra(10, pre_point-1, matrx)
            path = []
            f = now_point
            path.append(now_point)
            while f != 0:
                path.append(min_path[f-1])
                f = min_path[f-1]
            path.pop()
            print('Итак из точки № ', pre_point, ' , в точку № ', now_point, ' путь занял: ', min_weight[now_point-1], ' минут')
            print('А сам путь лежит через точки :')
            path = path[::-1]
            print(path)
            print('ПОЕХАЛИ!!!')
            input()
            for i in range(len(path)):
                turtle.goto(coordinats[path[i]-1][0], coordinats[path[i]-1][1])
                time.sleep(0.8)
            print('ПРИЕХАЛИ')
            input()
            os.system('cls')
        if len(visited) == 10:
            break
        counter += 1

    os.system('cls')
    print("""
          




          
          УРА!!! ПОЗДРАВЛЯЕМ! Вы прошли весь путь и ответили на все вопросы!

          Теперь можете взять с полки пирожок :)



                                                                """)


    print("Нажмите ENTER для выхода из программы")
    #turtle.done()
    input()
    
if (main == '__main__'):
    main()

