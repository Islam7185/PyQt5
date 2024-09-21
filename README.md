from PyQt5.QtCore import Qt
from PyQt5.QtWidgets import QApplication, QWidget, QPushButton, QLabel, QVBoxLayout

app = QApplication([])


class MyWindow(QWidget):
    def __init__(self, title, cor_x, cor_y, size_x, size_y, color=None, back_color=None):
        super().__init__()
        self.title = title
        self.cor_x = cor_x
        self.cor_y = cor_y
        self.size_x = size_x
        self.size_y = size_y
        self.color = color
        self.back_color = back_color

        self.set_appear()
        self.initUI()
        self.show()

    def set_appear(self):
        self.setWindowTitle(self.title)
        self.resize(self.size_x, self.size_y)
        self.move(self.cor_x, self.cor_y)

    def initUI(self):
            line = QVBoxLayout()
            txt = QLabel('Это надпись')
            btn = QPushButton('Это кнопка')
            line.addWidget(txt, alignment=Qt.AlignCenter)
            line.addWidget(btn, alignment=Qt.AlignCenter)
            self.setLayout(line)
    
    def set_style(self):
        if self.back_color and self.color:
              self.setStyleSheet('color: rgb' + str(self.color) +
                                 '; background-color: rgb' + str(self.back_color))
              
        elif self.color and not self.back_color:
            self.setStyleSheet('color: rgn' + str(self.color))

        elif self.back_color and not self.color:
             self.setStyleSheet('background-color: rgb' + str(self.back_color))



             
window1 = MyWindow('Окно 1', 100, 70, 500, 350, back_color=(255, 0, 255), color=(255,255,255))
window2 = MyWindow('Окно 2', 500, 300, 400, 400)
window3 = MyWindow('Окно 3', 500, 800, 150, 200)
window4 = MyWindow('Окно 4', 350, 200, 560, 345)
                   
app.exec()
