* Github andystu   Fork 複製一分到自己的儲存簿

* 將bootstrap_practice-master資料夾拉到sublime text3

* 搜尋sublime text3 package control  進入Installation - Package Control
* 複製以下文字
import urllib.request,os,hashlib; h = 'eb2297e1a458f27d836c04bb0cbaf282' + 'd0e7a3098092775ccb37ca9d6b2e4b7d'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)	

* 回到sublime: 按下ctrl+貼上複製的文字
* 安裝套件 1.Ctrl+shift+p→按第一個→emmet
           2.Ctrl+shift+P→Install→按第一個→html→HTML Beautify+ctrl+Alt+shift+F→可自動排版
           3.Ctrl+shift+P→Install→按第一個→Seti_UI

* 下載bootstrap 解壓縮檔案，拉進sublime

* 設計自己的網頁

* 開啟 index.html網頁(在網頁設定中選擇更多工具&rarr;編碼&rarr;自動偵測)就可以見證奇蹟囉!!

網頁設計語法
* 標題    
  <head>
  <title>_________<title>
  </head>

* 副標及內文
 <body>
 <h1>_______</h1>
  <p>________</p>
  </body>

* 按鈕button type='button'>打上你想要的字</button>

* 欄<div class=’col-md-□’>
  間格:加上< div class=’col-md-□’ col-md-offset-□'>

* 版面大小變換
 手機Extra Small col-xs-□
 平板Small     col-sm-□
 筆電Medium  col-md-□
 螢幕Large     col-lg-□
 Offset Class以此類推



