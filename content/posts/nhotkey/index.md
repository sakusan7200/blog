+++
title = 'Nhotkeyでタスクトレイにいながらキー入力を監視'
date = 2025-09-13T02:24:41+09:00
draft = true
+++

## NHotkeyとは
[リポジトリ](https://github.com/ranbims/NHotkey)

## 私がやろうとしたこと
タスクトレイに常駐中のWinUI3のアプリで、PrintScreenキーの入力でウィンドウを表示したい。

## インストール
```sh
dotnet add package NHotkey.WinUI --version 3.0.1
```

## 使い方
```c#
//using NHotkey.WindowsForms;
public MainWindow()
{
    InitializeComponent();

    //ウィンドウを閉じたと見せかけて非表示にする
    Closed += (sender, args) =>
    {
        args.Handled = true;
        this.Hide();
    };

    var keyAcc = new KeyboardAccelerator();
    keyAcc.Key = Windows.System.VirtualKey.Snapshot;
    keyAcc.Modifiers = Windows.System.VirtualKeyModifiers.None;//修飾キー無し

    //ここで
    HotkeyManager.Current.AddOrReplace("KeyDown", keyAcc, KeyDown);
}

private void KeyDown(object sender, HotkeyEventArgs e)
{
    Debug.WriteLine("KeyDown");
}
```

## はまったポイント
+ PrintScreenどれ？
    + Snapshot(まじでわからんかった)
