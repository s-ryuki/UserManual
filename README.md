ユーザーマニュアル
==================
　ここでは私たちが作成したRTC群の使用方法を説明します。
　  
モード切り替え
--------------
　　ロボットの開発には大きく分けて、まずロボットの動作と作成し、それをコントロールするという２つの操作が必要になります。  
　特にヒューマノイドロボットの場合、最初に歩行や旋回などといったモーションを作ってから、  
　実際にコントローラ等を用いる、または自律でそのモーションを再生するという方法をとります。  
　　私たちのRTMでは、ロボットの開発に必要な「モーション編集モード」と「モーション再生モード」の2つを使い分けることができます。  

###・モーション編集モード###
　　　ロボットを動作させる際にはロボットの動きを事前に作成しておく必要があります。  
　　ヒューマノイドロボットの場合は各関節の角度決定を行わなければなりません。  
　　そのため各ロボットメーカーはモーションエディタ等を用意し、ユーザーのモーション作成のサポートをしています。  
　　　本RTMでも、自作GUIを用いたモーションエディタを作成しました。  
####　　使用方法####
　　　　(1)OpenRTMの環境の整ったPCとロボットを以下のように接続します。  

　　　　　　　[![画像1][image1]](https://github.com/downloads/s-ryuki/Pictures/PC-Robot.png)
[image1]:https://github.com/downloads/s-ryuki/Pictures/PC-Robot.png

　　　　(2)ロボットを接続したPortのCOMを確認し、使用するサーボマネージャー(ex.PrsServoManager)のiniファイルのCOMを編集します。  
　　　　　また、iniファイルで使用するサーボモータの個数や可動域等を設定し、保存します。  

　　　　　　　　[![画像2][image2]](https://github.com/downloads/s-ryuki/Pictures/PrsServoManager_ini.png)
[image2]:https://github.com/downloads/s-ryuki/Pictures/PrsServoManager_ini.png
　　　　　　　　　　　　　　　　例：servomanager.ini（PrsServoManager）  
　  
　　　　(3)MotionEditor.pyおよび使用するサーボモーターに対応したサーボマネージャー(ex.PrsServoManager.py)を起動します。  
　  
　　　　(4)RTSystemEditorを起動し、MotionEditorとサーボマネージャを以下のように接続して、Activateします。  

　　　　　　　[![画像3][image3]](https://github.com/downloads/s-ryuki/Pictures/MotionEditor-PrsServoManager.png)
[image3]:https://github.com/downloads/s-ryuki/Pictures/MotionEditor-PrsServoManager.png

　　　　(5)MotionEditor上でモーションを作成し、最後にファイル出力をすれば完成です。  
####　　　　　　MotionEditorの使い方####
　　　　　　　　[![画像4][image4]](http://github.com/downloads/s-ryuki/Pictures/MotionEditor_GUI_Guide3.png)
[image4]:http://github.com/downloads/s-ryuki/Pictures/MotionEditor_GUI_Guide3.png

#####　　　　　　　画面説明#####
　　　　　　　　　　File：　出力するファイルの名前を入力  
　　　　　　　　　　Time：　サーボを目的角度まで動かすのにかける時間[ms]  
　　　　　　　　　　Wait：　目的角度に動いたあとの待機時間[ms]  
　　　　　　　　　　Pose：　作成するコマの番号  
　　　　　　　　　　　①：モーションファイル出力ボタン  
　　　　　　　　　　　②：全サーボモータON/OFFボタン  
　　　　　　　　　　　③：ポーズ出力ボタン  
　　　　　　　　　　　④：各サーボモータON/OFFボタン  
　　　　　　　　　　　⑤：サーボモータ角度調整ゲージ  
　　　　　　　　　　　⑥：ポーズ出力画面  
　  
　　　　　　　(1)サーボモータOn/OFFボタンですべてのサーボを保持させます。  
　　　　　　　(2)作成するPoseの各パラメータを設定します。  
　　　　　　　(3)各サーボモータのバーを左右に動かし、関節角度を決定します。  
　　　　　　　(4)すべての関節角度が決定したらPose出力ボタンをクリックし、右側にXML形式のモーションが作成されるのを確認します。  
　　　　　　　(5)Pose番号を変えて、同様にPoseを作成します。  
　　　　　　　(6)モーションが完成したらFile名を記入し、最後にFile出力ボタンをクリックします。  
　　　　　　　(7)MotionEditorのフォルダに作成したモーションファイルが生成されます。  
　  
　  
###・モーション再生モード###
　　　作成したモーションを再生します。以下のようにコンポーネントを接続してください。   
　　　　　　　　　　[![画像6][image6]](https://github.com/downloads/s-ryuki/Pictures/HumanInterface-PrsServoManager.png)
[image6]:https://github.com/downloads/s-ryuki/Pictures/HumanInterface-PrsServoManager.png
　　　　　　　　　　　　　　　例：HumanInterfaceコンポーネントを用いる場合
　  
　  
　　[![画像7][image7]](https://github.com/downloads/s-ryuki/Pictures/SimpleController-PrsServoManager.png)
[image7]:https://github.com/downloads/s-ryuki/Pictures/SimpleController-PrsServoManager.png
　　　　　　　　　　　　　　　　　　　例：SimpleControllerを用いる場合
　  
　  
　　　ロボットを操縦するためのコンポーネントとしてHumanInterfaceとSimpleControllerの2種類作成しました。  

####　　HumanInterfaceの使い方####
　　　　本コンポーネントはAndroid端末にインストールすることで使用可能になります。  
　　　　　　[![画像8][image8]](https://github.com/downloads/s-ryuki/Pictures/HumanInterface_GUI_Guide2.png)
[image8]:https://github.com/downloads/s-ryuki/Pictures/HumanInterface_GUI_Guide2.png
　　　　　　(1)使用するAndroid端末にアプリをインストールします。  
　　　　　　(2)アプリを立ち上げます。  
　　　　　　(3)IPアドレス欄に接続する先のIPアドレスを入力します。  
　　　　　　(4)「START」を押すと通信を開始し、PCのRTSytemEditor上にコンポーネントが表示されます。  
　　　　　　(5)上記のように繋ぎ、Activateします。  
　　　　　　(6)正常に接続されるとAndroid端末上に「onActivate」と表示され、使用可能となります。  
　　　　　　(7)各ボタンを押すことで、ボタンに割り振られたコマンドが送られ、MotionLoderで設定されたモーションが再生されます。  
　　　　　　(8)使用を終了するときは「STOP」ボタンを押せば接続が切れ、「Deactivete」と表示されます。  
   
####　　SimpleControllerの使い方####

　　　　　　[![画像9][image9]](https://github.com/downloads/s-ryuki/Pictures/SimpleController_GUI-Guide.png)
[image9]:https://github.com/downloads/s-ryuki/Pictures/SimpleController_GUI-Guide.png
　　　　　　(1)SimpleController.pyを起動します。  
　　　　　　(2)RTSystemEditor上で上記のように繋ぎます。  
　　　　　　(3)「サーボモータON」ボタンですべてのサーボを保持させます。  
　　　　　　(4)各ボタンを押すことで、ボタンに割り振られたコマンドが送られ、MotionLoderで設定されたモーションが再生されます。  
　  
　　　　　SimpleControllerは、作成したモーションを確かめる際に有用です。  
　　　　　別の端末と通信を行う必要がなく、簡単にモーションの確認が行えます。  