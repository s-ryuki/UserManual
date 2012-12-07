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
####　使用方法####
　　　　(1)OpenRTMの環境の整ったPCとロボットを以下のように接続します。  
　　　　
[![画像1][image1]](https://github.com/downloads/s-ryuki/Pictures/PC-Robot.png)
[image1]https://github.com/downloads/s-ryuki/Pictures/PC-Robot.png

　　　　(2)ロボットを接続したPortのCOMを確認し、使用するサーボマネージャーのiniファイルのCOMを編集します。  
　　　　　また、iniファイルで使用するサーボモータの個数や可動域等を設定し、保存します。  

[![画像2][image2]](https://github.com/downloads/s-ryuki/Pictures/PrsServoManager_ini.png)
[image2]https://github.com/downloads/s-ryuki/Pictures/PrsServoManager_ini.png

　　　　(3)MotionEditor.pyおよび使用するサーボモーターに対応したサーボマネージャー(ex.PrsServoManager)を起動します。
　　　　(4)RTSystemEditorを起動し、MotionEditorとサーボマネージャを以下のように接続して、Activateします。
[![画像3][image3]]()
[image3]
　　　　(5)MotionEditor上でモーションを作成し、最後にファイル出力をすれば完成です。
[![画像4][image4]]()
[image4]
　  
　  
#####　MotionEditorの使い方######


　　　　①ServoOn/OFFボタンですべてのサーボを保持させます。
　　　　②


###・モーション再生モード###
　　　作成したモーションを再生します。以下のようにコンポーネントを接続してください。  
[![画像5][image5]]()
[image5]

[![画像6][image6]]()
[image6]

　　　ロボットを操縦するコントローラとしてHumanInterfaceとSimpleControllerの２種類作成しました。  
　　HumanInterfaceはAndroid端末にインストールすれば、端末からロボットの操縦が可能です。  
　　また、作成したモーションを確かめる際にはSimpleControllerをご使用できます。  
　　Android端末との通信を行う必要がなく、簡単にモーションの確認が行えます。  
　