# Getting Started

* [本地端撰寫文件](#本地端撰寫文件)
* [編譯成靜態檔案](#編譯成靜態檔案)
* [發佈](#發佈)


## 本地端撰寫文件

#### 安裝 Gitbook

安裝 [gitbook](http://toolchain.gitbook.com/setup.html) 套件需要 Node.js 環境與 NPM，在此已假設這兩項需求皆已安裝完畢。

```
npm install gitbook-cli -g
```

#### 預覽文件

本地端預覽 gitbook 內容 ( 此步驟會將 gitbook 內的 [.md](https://guides.github.com/features/mastering-markdown/) 檔編譯成 .html 檔 )。執行以下指令後，即可於瀏覽器開啟 http://localhost:4000 預覽

```
gitbook serve
```


## 編譯成靜態檔案

#### 打包文件

專寫完成後，可將文件打包成靜態 HTML 檔

```
gitbook build
```

更多詳細的說明，請參考

* [Setup and Installation of GitBook](http://toolchain.gitbook.com/setup.html)


## 發佈

Gitbook 可將 markdown 文件編譯成靜態的 html 檔，我們可以使用 nginx 來 serve 靜態的 html 檔。發佈流程包含以下三個步驟

* gitbook build
* docker-compose build
* docker-compose up -d

以上三個步驟可於 deploy.sh 執行

```
./deploy.sh
```
