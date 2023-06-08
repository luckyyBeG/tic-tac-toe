# tic-tac-toe
print("Добро пожаловать в игру крестики-нолики!")
print("Пустые ячейки пронумерованы числами от 1-9 следущим образом:")
print(" 1 2 3")
print(" 4 5 6")
print(" 7 8 9")
print("чтобы слелать ход выберите цифру")
field = [" " for i in range(10)] #Задаем количество ячеек

def showfield(field): # Функция показывает изначальное игровое поле
   print(" ", 0, " ", 1, " ", 2)
   for i in range(3):
      print("|", field[0+i*3], "|", field[1+i*3], "|", field[2+i*3], "|")


def take_input(player_token):#
   valid = False#
   while not valid: #
      player_answer = input("Делает ход " + player_token + " ")#
      try:
         player_answer = int(player_answer)#
      except:
         print("Введите число")
         continue
      if player_answer >= 1 and player_answer <= 9:
         if(str(field[player_answer-1]) not in "XO"):
            field[player_answer-1] = player_token
            valid = True
         else:
            print("Эта клетка уже занята!")
      else:
        print("Некорректный ввод. Введите число от 1 до 9.")

def who_win(field):
   win_num = ((0,1,2), (3,4,5), (6,7,8), (0,3,6), (1,4,7), (2,5,8), (0,4,8), (2,4,6))
   for a in win_num:
       if field[a[0]] == field[a[1]] == field[a[2]]:
          return field[a[0]]
   return False

def game(field):
    count = 0
    win = False
    while not win:
        showfield(field)
        if count % 2 == 0:
           take_input("X")
        else:
           take_input("O")
        count += 1
        if count > 4:
           b = who_win(field)
           if b:
              print(b, "выиграл!")
              win = True
              break
        if count == 9:
            print("Ничья!")
            break
    showfield(field)
game(field)

input("Нажмите Enter для выхода!")
