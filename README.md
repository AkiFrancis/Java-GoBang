# Java-GoBang
利用java开发的联机五子棋

## 概述
  这是一款支持联机的五子棋游戏，具有基本的五子棋功能（悔棋、重新开始、存储棋谱、回放棋谱），并且目前有两种游戏模式（单机游戏、联机游戏）
  
## 单机模式 
  用户开启游戏后要先选择游戏模式，如果选择单机模式，则可以自行在棋盘上下棋，可以进行悔棋、重新开始、存储棋谱、回放棋谱等操作（棋谱保存在本地）
  
## 联机模式
  联机模式的开启方法比较特别，需要先开启服务端进程GoBang_Server，选择联机模式，等待客户端的连接
  GoBang_Server已建立的情况下，用户可以打开客户端进程GoBang_Client，选择联机模式，会连接到服务器，此后即可开始对局
  · 这里需要注意一点，在进行连接时，如果不在同一台主机进行客户端和服务器的启动，则需要将客户端Online_Button_Listener类中的函create_thread中的Socket连接的"localhost"更改为你的服务器程序所在的网络IP地址
  · 这里只支持在同一个SA下的联机游戏，无法穿越网关
  联机模式下由服务端执黑，先落子；客户端执白，后落子
  两边都可以在下完一步棋但是对方还未下下一步棋时向对方发起悔棋请求，需要得到对方同意
  同样的，也可以申请重新开始，同样需要得到对方同意
  
## 断开连接
  在联机模式下，如果需要安全地断开连接，则按下断开连接按钮，可以与服务器或客户端断开连接，此后可以再次点击联机模式尝试连接，或者选择单机模式进行游戏
  
## 保存棋谱
  每局游戏进行时、结束后都可以进行保存棋谱的操作，给它命名后会在本地的chess_logs文件夹中以txt文档的形式保存本局的棋谱

## 回放棋谱
  回放棋谱要在单机模式下进行，可以选择保存的棋谱，随后会载入棋谱，点击下一步按钮可以进行行棋，当棋谱走完，就不能进行下一步了
