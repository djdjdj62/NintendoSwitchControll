# NintendoSwitchController
# 用arduino 模擬 Joycon 控制 switch 

## 所需條件:

1. arduino leonardo 系列的產品(必定要是 atmega32u4)

2. usb to type-c
 
### 參考網站:

https://github.com/interimadd/NintendoSwitchControll

https://kokenikki.blogspot.com/2021/02/arduino01arduino-leonardo.html

## arduino 設定:

### 修改 boards.txt:
leonardo.name=Arduino Leonardo 下所有的 leonardo.vid&pid 都改成這樣

leonardo.vid.0= 0x0f0d
leonardo.pid.0= 0x0092
包含(leonardo.upload_port.0.vid)

### 燒錄板子選擇 

Arduino AVR Boards -> Arduino Leonard

### 函示庫介紹:

##### 按鈕操控方法:
void pushButton(Button button, int delay_after_pushing_msec, int loop_num=1);          按鈕控制
void push2Button(Button button1,Button button2, int delay_after_pushing_msec, int loop_num=1); 同時按下兩個按鈕
void pushHatButton(Hat button, int delay_after_pushing_msec, int loop_num=1);          十字鈕控制
void pushHatButtonContinuous(Hat button, int pushing_time_msec);                       十字鈕持續控制
void tiltJoystick(int lx_per, int ly_per, int rx_per, int ry_per, int tilt_time_msec); 左/右搖桿控制
###### 按鈕控制的名稱:
  Y,
  B,
  A,
  X,
  L,
  R,
  ZL,
  ZR,
  MINUS,
  PLUS,
  LCLICK,
  RCLICK,
  HOME,
  CAPTURE
###### 十字紐控制的名稱:
  UP,
  UP_RIGHT,
  RIGHT,
  RIGHT_DOWN,
  DOWN,
  DOWN_LEFT,
  LEFT,
  LEFT_UP,
  CENTER
###### 左搖桿用"十字向量(四個座標)來控制方向"
##### 各函示使用範例:
pushButton(Button::A, 1500, 2); 其他所有按鈕
pushButton( 按鈕 , 持續時間 , 次數);

push2Button(Button::B,Button::Y, 0, 1); 同時按下兩個按鈕
pushButton( 按鈕      , 按鈕     , 持續時間 , 次數);

pushHatButton(Hat::RIGHT, 500); 十字按鈕
pushHatButton( 十字按鈕, 持續時間 );

pushHatButtonContinuous(Hat::LEFT_UP, 1000); 十字按鈕
pushHatButtonContinuous( 十字按鈕 , 時間);

tiltJoystick(100, 100, -100, -100, 3000); 左/右搖桿
tiltJoystick(左X, 左Y , 右X , 右Y , 持續時間(X/1000)秒);
