---
title: '[Python] - PyQt - QThread'
updated: 2024-12-18 15:35:12Z
created: 2023-10-20 13:22:46Z
latitude: 22.64839560
longitude: 120.32620850
altitude: 0.0000
tags:
  - pyqt
  - threads
---

# PyQt - QThread

## 筆記
利用Qthread 是為了GUI 卡死 
除了PyQt5 中的Qthread ,在一般的PYTHON 使用中，也可以引用 Threading 這個套件去做平行處理

- 所使用執行緒的數量依據cpu 的數量決定
- 最好可以重複回收使用這些被定義的 Thread

### Thread 應用的狀況
- Race conditions 
> Occur when threads access shared state. Can cause intermittent bugs. Use mutexes/locks to control access.

- Deadlocks
> Threads waiting on each other for locks. Carefully structure lock order and releases
- UI Freezing
> Heavy processing in main thread blocks UI updates. Use worker threads/QThread.
- Shared resource access
> Use Queues or conditional variables to safely pass data between threads.
- Uncaught exceptions
> Exceptions in threads may go unnoticed. Catch them and log/display them.

---
# Signals & Slots

當某個事件發生 > 發出通知的訊息 (Signals)
當收到某個通知(Signals) > 觸發引起的動作 (Slots)

## Home work 
修改以下範例，改成某個函數
或是輸入檔案的資料

- 鑲嵌到自己設計的介面中
 Example 1. Progress Bar 
 
 <details>
 <summary>Code</summary>
 
 ```python
from PyQt5.QtCore import *
from PyQt5.QtGui import *
from PyQt5.QtWidgets import *
import sys, time

class Main(QMainWindow):
    def __init__(self):
        super().__init__()
        self._isrunning = False
        MyLbl = QLabel('Task Progress')
        MyWidget = QWidget()
        self.setWindowTitle('Test QThread')
        MyWidget.resize(300,200)
        StartBtn = QPushButton('Start',MyWidget)
        StopBtn = QPushButton('Stop',MyWidget)
        layout = QVBoxLayout()
        max_val , min_val = 100, 0
        self.progressBar = QProgressBar(MyWidget)
        self.progressBar.setVal = 0
        self.progressBar.setRange(min_val,max_val)
        
        StartBtn.clicked.connect(self.procStart)
        StopBtn.clicked.connect(self.procStop)
        layout.addWidget(MyLbl)
        layout.addWidget(self.progressBar)        
        layout.addWidget(StartBtn)
        layout.addWidget(StopBtn)
        MyWidget.setLayout(layout)
        self.setCentralWidget(MyWidget)
        self.worker =Worker(max_val ,min_val)
        
    def procStart(self):
        self._isrunning =True
        print('the worker start the job')
        self.worker.signal.connect(self.grab_data)
        self.worker.run()
       
    def procStop(self):
        self._isrunning = False
        print('the worker stop the job')
        self.worker.stop()

    @pyqtSlot(object)
    def grab_data(self, data):
        self.progressBar.setValue(int(data))

class Worker(QThread):
    signal = pyqtSignal(object)

    def __init__(self,max,min):
        super().__init__()
        self._isrunning = True
        self.max = max 
        self.min = min
    def run(self):
        i = 1
        while self._isrunning:
            if i < self.max:
                time.sleep(0.1)
                i += 5
                self.signal.emit(i)
            else: 
                i = self.max
                self.signal.emit(i)
                print('the val reach the lmit, worker is going to end... ')
                break

    def stop(self):
        print('the worker is going to stop')
        self.quit

if __name__ == "__main__": 
    app = QApplication(sys.argv)
    widget = Main()
    widget.show()
    sys.exit(app.exec_())
```
 </details>


---
Example 2. Grab the pc camera 

```python
# 2023.Dec.20 
from PyQt5.QtCore import *
from PyQt5.QtGui import *
from PyQt5.QtWidgets import * 
from PyQt5 import uic 
import sys, cv2 

#-----
'''
todo 
- [x] slider bar value connect to thres value 
- remove the redundant parts and reorganize 
- [x] connect to webcam 
'''
#----
 
class MainWindow(QMainWindow):
	def __init__(self):
		super(MainWindow,self).__init__()
		uic.loadUi('Pool.ui',self)
		self.pwd = r'D:\personal\demo_proj\ChangProj\opencv_test' 
		self.CloseBtn.clicked.connect(self.CancelFeed)
		self.StartBtn.clicked.connect(self.OnClick)
		self.LoadBtn.clicked.connect(self.OpenFile)
		self.ThresSlider.sliderMoved.connect(self.slider_position)
		self.ThresVal.setText('90')
		self.worker = Worker1(self.ThresVal.text())
		self.worker.window = self
		self.ThresSlider.sliderMoved.connect(self.slider_position)

	def OnClick(self):
		self.make_connection(self.worker)
		self.worker.start()

	def make_connection(self,data_obj):
		data_obj.ImageUpdate.connect(self.grab_pic)

	@pyqtSlot(object)
	def grab_pic(self,img):
		self.ImgLabel.setPixmap(QPixmap.fromImage(img[0]))
		self.OImgLabel.setPixmap(QPixmap.fromImage(img[1]))

	def slider_position(self,p):
		self.ThresVal.setText(str(p))
		
	def CancelFeed(self):
		self.worker.stop()
		cv2.destroyAllWindows()

	def OpenFile(self):
		img, _ = QFileDialog.getOpenFileName(self,'select you file',self.pwd, 'all files (*); image files(*.jpg)')
		Qimage = QImage(img)
		Resize_QImage = QPixmap.scaled(self.ImgLabel.size(), Qt.KeepAspectRatio)
		self.ImageUpdateSlot(Resize_Qimage)

class Worker1(QThread):
	ImageUpdate = pyqtSignal(object)

	def __init__(self,val):
		super(Worker1,self).__init__()
		self.Thres = int(val)
		# print(type(self.Thres))
	def run(self):
		self.ThreadActive = True
		self.Cap = cv2.VideoCapture(0,cv2.CAP_DSHOW)
		print(self.Thres)	
		while self.ThreadActive:
			ret, frame = self.Cap.read()
			self.Thres = self.window.ThresSlider.value()
			if ret:
				GRAY =  cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
				Convert2QtFormat = QImage(GRAY.data, GRAY.shape[1],GRAY.shape[0],QImage.Format_Indexed8)
				_ , ThresImg = cv2.threshold(GRAY,self.Thres,255,cv2.THRESH_BINARY)
				Thres2QtFormat = QImage(ThresImg.data,ThresImg.shape[1],ThresImg.shape[0],QImage.Format_Indexed8)
			
			self.ImageUpdate.emit([Convert2QtFormat,Thres2QtFormat])

	def stop(self):
		self.ThreadActive = False 
		self.Cap.release()
		cv2.destroyAllWindows()
		self.quit()
	
if __name__ == '__main__':
	Ap = QApplication(sys.argv)
	Root =MainWindow()
	Root.show()
	sys.exit(Ap.exec_())
		
```


ex 3.  progress bar 
```python
from  PyQt5.QtWidgets import *
from PyQt5.QtCore import * 
import sys, time
import random 

class Download(QMainWindow):
    def __init__(self):
        super(Download,self).__init__()
        self.setWindowTitle('Download win')
        # init parameters 
        self.b_progress = False
 
        # init ui interface 
        self.initUi()
        self.resize(800,600)
 
    def initUi(self):
        self.ok_btn = QPushButton('Start Download')
        self.stop_btn = QPushButton('Stop')
        self.cancel_btn = QPushButton('Close')

        self.progress_Bar = QProgressBar()
        self.progress_Bar.setRange(0,100)
        self.progress_Bar.setValue(0)

        layout = QVBoxLayout()
        layout.addWidget(self.progress_Bar)
        layout.addWidget(self.ok_btn)
        layout.addWidget(self.stop_btn)
        layout.addWidget(self.cancel_btn)
        
        Mywidget = QWidget()
        Mywidget.setLayout(layout)

        self.setCentralWidget(Mywidget)
 
        # bind the function 
        self.ok_btn.clicked.connect(self.start_progress)
        self.stop_btn.clicked.connect(self.stop_progress)
        self.cancel_btn.clicked.connect(self.end_progress)

    def start_progress(self):
        self.ok_btn.setEnabled(False)
        self.stop_btn.setEnabled(True)
 
        self.b_progress = True
        try:
            print('the process is going to start')
            print('worker start working now')
            self.worker = Myworker()
            self.worker.myflag.connect(self.progress_run)
            self.worker.start()
        except:
            self.worker = Myworker()
            self.worker.start()
 
    def stop_progress(self):
        print('the stop button is pressed')
        self.b_progress = False
        if self.worker:
            self.worker.stop()
 
        self.on_workerfinish()

    def on_workerfinish(self):
        self.ok_btn.setEnabled(True)
        self.stop_btn.setEnabled(False)
        self.progress_Bar.setValue(0)


    def end_progress(self):
        if self.worker:
            self.worker.stop()
            self.worker.wait()

        self.MessageBox()
        self.close()

    @pyqtSlot(object)
    def progress_run(self,i):
        self.progress_Bar.setValue(i)

    def MessageBox(self):
        msg = QMessageBox()
        msg.setIcon(QMessageBox.Icon.Information)
        msg.setText('The window is going to close')
        msg.exec()
        
class Myworker(QThread):
    myflag = pyqtSignal(object)
    def __init__(self):
        super().__init__()
        self._isrunning = True
        print('init the worker')

    def run(self):
        while self._isrunning:
            for i in range(11):
                time.sleep(0.5)
                self.myflag.emit(i*10)
            self._isrunning = False

    def stop(self):
        self._isrunning =False
        print('the worker is going to stop')
        self.wait()



if __name__ == '__main__':
    MyWin = QApplication(sys.argv)
    root=  Download()
    root.show()
    sys.exit(MyWin.exec_())
    

    


```



---
## 問題

- 在 worker 的 class 中為何會常見到一個寫法，代表什麼?
```python
class MyWorker(QThread)
	def __init__(self):
		super(MyWorker,self).__init__()
		# super().__init()
```
- worker class 中 如果沒有加 super().__init__() 會出現錯誤，是什麼原因?
>RuntimeError: super-class __init__() of type Worker was never called

這一行用意在於初始化QThread，去設定好內部所需要用到關於thread function. 因此，如果沒有加，就會出現錯誤。
另外，super(Worker,self).__init__() 也可以打成super().__init__()。只是這樣比較精確。

- PyQt thread 的信號可以同時送給兩個甚至更多個 slot 嗎?
> 可以。

### review of ex.3 
- self.worker 應該在init 被宣告, 還是在被按下按鈕後？
目前測試, 需要建立在按下按鈕後

- start 和 stop button 彼此間需要去互鎖
!! 需要找更簡單的機制
設計時還要考量重置與 continue 的機制

- 原本當沒有把 progress 的計算寫到 worker 中 , 一按下開始, 其他按鈕就要等到progress bar finish 才能使用

- worker 啟動是worker.start() 不是 worker.run()

- worker stop 時, 需要加上 worker.wait()





---
## 閱讀
- [ ] https://www.pythontutorial.net/pyqt/pyqt-qthread/
- [ ] https://realpython.com/python-pyqt-qthread/
- [x] https://steam.oxxostudio.tw/category/python/pyqt5/qthread.html
 
- [ ] [Python concurency](https://www.pythontutorial.net/python-concurrency/)
- [ ] [Python THread](https://www.pythontutorial.net/pyqt/pyqt-qthread/)
- [ ] [知乎 - Python thread 中文說明](https://zhuanlan.zhihu.com/p/53270619)
- [ ] [知乎 - QT 中的 Multi Thread](https://zhuanlan.zhihu.com/p/52612180)

## 資源
- [Qt designer](https://realpython.com/qt-designer-python/)
- [Python QT Document](https://doc.qt.io/qtforpython-6/index.html)



