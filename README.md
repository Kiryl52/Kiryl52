Interface
from PyQt5.QtWidgets import (
    QApplication, QWidget, QLabel, QPushButton,QVBoxLayout,QHBoxLayout,QSizePolicy
)
from PyQt5.QtCore import Qt

app = QApplication([])
window = QWidget()
window.setFixedSize(335, 400)
window.setWindowTitle("Калькулятор") 

app.setStyleSheet("""
                  QWidget {background-color: #00FFFF;}
                  QPushButton {background-color: #008B8B; border-radius:10px;font-size:25px; border-style: outset;}
                  QPushButton:pressed {background-color: #808080 ;border-style: inset}
                  QLabel {font-size:35px}
                  """)



result = QLabel("0")

b1 = QPushButton("1")
b2 = QPushButton("2")
b3 = QPushButton("3")
b4 = QPushButton("4")
b5 = QPushButton("5")
b6 = QPushButton("6")
b7 = QPushButton("7")
b8 = QPushButton("8")
b9 = QPushButton("9")
b0 = QPushButton("0")

b_plus = QPushButton("+")
b_minus = QPushButton("-")
b_multiply = QPushButton("*")
b_divine = QPushButton("/")
b_point = QPushButton(".")
b_equals = QPushButton("=")
b_bacspace = QPushButton("<-")
b_clear = QPushButton("C")
b_power = QPushButton("x^y")
b_percent = QPushButton("%")

b1.setSizePolicy(QSizePolicy.Minimum, QSizePolicy.Minimum)
b2.setSizePolicy(QSizePolicy.Minimum, QSizePolicy.Minimum)
b3.setSizePolicy(QSizePolicy.Minimum, QSizePolicy.Minimum)
b4.setSizePolicy(QSizePolicy.Minimum, QSizePolicy.Minimum)
b5.setSizePolicy(QSizePolicy.Minimum, QSizePolicy.Minimum)
b6.setSizePolicy(QSizePolicy.Minimum, QSizePolicy.Minimum)
b7.setSizePolicy(QSizePolicy.Minimum, QSizePolicy.Minimum)
b8.setSizePolicy(QSizePolicy.Minimum, QSizePolicy.Minimum)
b9.setSizePolicy(QSizePolicy.Minimum, QSizePolicy.Minimum)
b0.setSizePolicy(QSizePolicy.Minimum, QSizePolicy.Minimum)
b_plus.setSizePolicy(QSizePolicy.Minimum, QSizePolicy.Minimum)
b_minus.setSizePolicy(QSizePolicy.Minimum, QSizePolicy.Minimum)
b_multiply.setSizePolicy(QSizePolicy.Minimum, QSizePolicy.Minimum)
b_divine.setSizePolicy(QSizePolicy.Minimum, QSizePolicy.Minimum)
b_equals.setSizePolicy(QSizePolicy.Minimum, QSizePolicy.Minimum)
b_power.setSizePolicy(QSizePolicy.Minimum, QSizePolicy.Minimum)
b_point.setSizePolicy(QSizePolicy.Minimum, QSizePolicy.Minimum)
b_percent.setSizePolicy(QSizePolicy.Minimum, QSizePolicy.Minimum)
b_bacspace.setSizePolicy(QSizePolicy.Minimum, QSizePolicy.Minimum)
b_clear.setSizePolicy(QSizePolicy.Minimum, QSizePolicy.Minimum)

layout1 = QHBoxLayout()
layout1.addWidget(b_percent)
layout1.addWidget(b0)
layout1.addWidget(b_point)
layout1.addWidget(b_equals)

layout2 = QHBoxLayout()
layout2.addWidget(b1)
layout2.addWidget(b2)
layout2.addWidget(b3)
layout2.addWidget(b_plus)

layout3 = QHBoxLayout()
layout3.addWidget(b4)
layout3.addWidget(b5)
layout3.addWidget(b6)
layout3.addWidget(b_minus)

layout4 = QHBoxLayout()
layout4.addWidget(b7)
layout4.addWidget(b8)
layout4.addWidget(b9)
layout4.addWidget(b_multiply)

layout5 = QHBoxLayout()
layout5.addWidget(b_divine)
layout5.addWidget(b_power)
layout5.addWidget(b_clear)
layout5.addWidget(b_bacspace)

main_layout = QVBoxLayout()
main_layout.addWidget(result, alignment= Qt.AlignRight)
main_layout.addLayout(layout5)
main_layout.addLayout(layout4)
main_layout.addLayout(layout3)
main_layout.addLayout(layout2)
main_layout.addLayout(layout1)

window.setLayout(main_layout)

window.show()
#################Main

from interface import *


class Calc():
    def __init__(self):
        self.point = 0
        self.action = False
        self.actions = ["+","-","*","/","%", "^"]

calc = Calc()

def clicked_0():
    if result.text() != "0":
        result.setText(result.text() + "0")

def clicked_1():
    if result.text() != "0":
        result.setText(result.text() + "1")
    else:
        result.setText("1")
def clicked_2():
    if result.text() != "0":
        result.setText(result.text() + "2")
    else:
        result.setText("2")
def clicked_3():
    if result.text() != "0":
        result.setText(result.text() + "3")
    else:
        result.setText("3")
def clicked_4():
    if result.text() != "0":
        result.setText(result.text() + "4")
    else:
        result.setText("4")
def clicked_5():
    if result.text() != "0":
        result.setText(result.text() + "5")
    else:
        result.setText("5")
def clicked_6():
    if result.text() != "0":
        result.setText(result.text() + "6")
    else:
        result.setText("6")
def clicked_7():
    if result.text() != "0":
        result.setText(result.text() + "7")
    else:
        result.setText("7")
def clicked_8():
    if result.text() != "0":
        result.setText(result.text() + "8")
    else:
        result.setText("8")
def clicked_9():
    if result.text() != "0":
        result.setText(result.text() + "9")
    else:
        result.setText("9")

def clicked_plus():
    if calc.action and result.text()[-1] in calc.actions:
        result.setText(result.text()[:-1] + "+")
    else:
        if calc.action:
            clicked_equals()
            pass
        if result.text()[-1] == ".":
            result.setText(result.text()[:-1])
        result.setText(result.text() + "+")
        calc.action = True
        calc.point = 1
      
def clicked_minus():
    if calc.action and result.text()[-1] in calc.actions:
        result.setText(result.text()[:-1] + "-")
    else:
        if calc.action:
            clicked_equals()
            pass
        if result.text()[-1] == ".":
            result.setText(result.text()[:-1])
        result.setText(result.text() + "-")
        calc.action = True
        calc.point = 1

def clicked_percent():
    if calc.action and result.text()[-1] in calc.actions:
        result.setText(result.text()[:-1] + "%")
    else:
        if calc.action:
            clicked_equals()
            pass
        if result.text()[-1] == ".":
            result.setText(result.text()[:-1])
        result.setText(result.text() + "%")
        calc.action = True
        calc.point = 1

def clicked_multiply():
    if calc.action and result.text()[-1] in calc.actions:
        result.setText(result.text()[:-1] + "*")
    else:
        if calc.action:
            clicked_equals()
            pass
        if result.text()[-1] == ".":
            result.setText(result.text()[:-1])
        result.setText(result.text() + "*")
        calc.action = True
        calc.point = 1

def clicked_divine():
    if calc.action and result.text()[-1] in calc.actions:
        result.setText(result.text()[:-1] + "/")
    else:
        if calc.action:
            clicked_equals()
            pass
        if result.text()[-1] == ".":
            result.setText(result.text()[:-1])
        result.setText(result.text() + "/")
        calc.action = True
        calc.point = 1

def clicked_point():
    if not calc.action and calc.point == 0:
        result.setText(result.text() + ".")
        calc.point = 1
    elif calc.action and calc.point == 1:
        if result.text()[-1] in calc.actions:
            result.setText(result.text() + "0.")
        else:
            result.setText(result.text() + ".")
        calc.point = 2

def clicked_power():
    if result.text() != "0":
        result.setText(result.text() + "^")
    calc.action = True
    calc.point = 1        
        
def clicked_clear():
    calc.action = False
    calc.point = 0
    result.setText("0")

def clicked_backspace():
    if len(result.text()) == 1:
        result.setText("0")
    elif result.text()[-1] == ".":
        calc.point -= 1
        result.setText(result.text()[:-1]) 
    elif result.text()[-1] in calc.actions:
        calc.action = False
        result.setText(result.text()[:-1]) 
    else:
        result.setText(result.text()[:-1]) 


def clicked_equals():
    if calc.action:
        index = 0
        for element in result.text():
            if element in calc.actions:
                break
            index += 1
        if not (len(result.text()) > index + 1):
            result.setText(result.text() + "0")
        first_value = float(result.text()[:index])
        second_value = float(result.text()[index + 1:]) 
        action = result.text()[index]

        if action == "+":
            result.setText(str(first_value + second_value))
        elif action == "-":  
            result.setText(str(first_value - second_value))
        elif action == "*":  
            result.setText(str(first_value * second_value))
        elif action == "%":
            result.setText(str(first_value / 100))
        elif action == "/":  
            if second_value == 0:
                result.setText("На 0 не ділиться")
            else:
                result.setText(str(first_value / second_value))
        if result.text()[-2:] == ".0":
            result.setText(result.text()[:-2])  

        elif action == "^":
            second_value = int(second_value - 1)
            res = first_value
            for i in range(second_value):
                res = res * first_value
            result.setText(str(res))



b_power.clicked.connect(clicked_power)
b_percent.clicked.connect(clicked_percent)
b_equals.clicked.connect(clicked_equals)
b_divine.clicked.connect(clicked_divine)
b0.clicked.connect(clicked_0)
b_divine.clicked.connect(clicked_divine)
b_multiply.clicked.connect(clicked_multiply)
b_plus.clicked.connect(clicked_plus)
b_minus.clicked.connect(clicked_minus)
b_point.clicked.connect(clicked_point)
b_clear.clicked.connect(clicked_clear)
b_bacspace.clicked.connect(clicked_backspace)
b1.clicked.connect(clicked_1)
b2.clicked.connect(clicked_2)
b3.clicked.connect(clicked_3)
b4.clicked.connect(clicked_4)
b5.clicked.connect(clicked_5)
b6.clicked.connect(clicked_6)
b7.clicked.connect(clicked_7)
b8.clicked.connect(clicked_8)
b9.clicked.connect(clicked_9)


app.exec_()
