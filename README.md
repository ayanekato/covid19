# コロナ陽性者数予測概要

この分析の概要は、中妻研究会Data Science Part の入ゼミ課題として、googleが発表している[Japan COVID-19 Forecast](https://datastudio.google.com/u/0/reporting/8224d512-a76e-4d38-91c1-935ba119eb8f/page/ncZpB?s=nXbF2P6La2M) を元にデータセットを作成し、pythonとAutoMLでそれぞれコロナウイルスの感染拡大予測を行って、***①Google予測値***, ***②pythonで手組みした予測値***, ***③AutoMLが算出した予測値*** の3つを実績値と比較して精度比較を行うというものです。　※考察はプレゼン資料にてまとめて行っています。

+ 学習期間         ：2020/02/04 ~ 2020/11/28

+ 予測対象期間 ：2020/11/29 ~ 2020/12/26 

以下では各フォルダの概要を示します。



## 00_元データとデータセットの作成過程

このフォルダには以下のcsvファイル、jupyter notebookが格納してあります。

+ [Japan COVID-19 Forecast](https://datastudio.google.com/u/0/reporting/8224d512-a76e-4d38-91c1-935ba119eb8f/page/ncZpB?s=nXbF2P6La2M) のデータソースの内、利用できそうだった以下9つのcsvファイル（データセットの元データ）
  + cases_total.csv
  + death_total.csv
  + effective_reproduction_number.csv
  + pcr_case_daily.csv
  + pcr_positive_daily.csv
  + pcr_tested_daily.csv
  + prefectures.csv
  + recovery_total.csv
  + severe_daily.csv

+ 上記のcsvを加工・集計して、データセットにまとめる作業を示したjupyter notebook
  + データセット作成過程.ipynb

+ 上記の「データセット作成過程.ipynb」により作成されたデータセット
  + automl_data
  + sarima_data
  + training_set.csv
  + test_set.csv



## 01_Googleの予測値

ここではGoogleサイトでダウンロードしたcsvから必要な部分を抽出する作業を行っています。
このフォルダには以下のcsvファイル、jupyter notebookが格納してあります。

+ [Google COVID-19 感染予測(日本版)](https://datastudio.google.com/u/0/reporting/8224d512-a76e-4d38-91c1-935ba119eb8f/page/ncZpB?s=nXbF2P6La2M)からダウンロードしてきたGoogleの予測値が含まれたcsvファイル
  + google1129_1226.csv

+ 上記のcsvを加工・集計して、Googleの28日後予測値を抽出する作業を示したjupyter notebook
  + google_predict.ipynb

+ 上記の「Googleの予測値.ipynb」により作成された、Googleの予測値を格納したcsv
  + google_predict.csv



## 02_Pythonでの予測値

ここでは[00_元データとデータセットの作成過程](#00_元データとデータセットの作成過程)で作成したデータセットを使い、SARIMAモデルで予測を行っています。
このフォルダには以下のcsvファイル、jupyter notebookが格納してあります。

+ Python（SARIMA）で予測するためのデータセット
  + sarima_data.csv

+ 上記のcsvを利用してモデリングする過程を示したjupyter notebook
  + sarima_predict.ipynb

+ 上記の「sarima_predict.ipynb」により推定された、Pythonでの予測値を格納したcsv
  + sarima_predict.csv



## 03_AutoMLでの予測値

ここでは[00_元データとデータセットの作成過程](#00_元データとデータセットの作成過程)で作成したデータセットを使い、AutoMLで予測を行っています。※AutoMLの分析過程はプレゼン資料に記載
このフォルダには以下のcsvファイルが格納してあります。

+ AutoMLに投入したデータセット
  + automl_data.csv

+ AutoMLが推定した予測値を格納したcsv
  + automl_predict.ipynb



## 04_予測結果の集計と比較

このフォルダには以下のExcelファイルが格納してあります。

+ 以上3つの予測結果（+おまけの予測結果）精度を表とグラフで比較したもの
  + 予測結果の集計と比較.xlsx



## 99_予測結果の集計と比較

こちらは ***02_SARIMAでの予測*** をする前に、予測期間の説明変数使って回帰をしてしまって没としたものを格納しています。予測期間の説明変数使っているから実運用が不可能で予測値には意味がないですが、データの前処理や特徴洗い出しは丁寧に説明してあるので、ここにおまけとして供養しておきました。　
ご興味あればご覧ください。

このフォルダには以下のcsvファイル、jupyter notebookが格納してあります。

+ 学習用データセット（期間：2020/02/04 ~ 2020/11/28）
  + training_set.csv

+ 予測用データセット（期間：2020/11/29 ~ 2020/12/26）
  + test_set.csv

+ 分析過程を示したjupyter notebook
  + python_predict.ipynb

