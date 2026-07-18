# 錢庭羽 聯絡頁 → GitHub Pages 部署步驟

這個資料夾裡只有一個 `index.html`,是照名片風格做的單頁聯絡頁(大頭照 / 姓名職稱 / Call·Email·Directions 按鈕 / 聯絡明細)。用 GitHub Pages 部署後拿到的網址,就可以拿去產生 QR code。

## 1. 換上真實照片(可選)

目前大頭照是文字佔位(圓圈裡一個「錢」字)。要換成真實照片或公司 logo:

1. 把圖片檔案(建議命名 `logo.png`)放進這個資料夾,跟 `index.html`同一層。
2. 打開 `index.html`,找到這一段(大約在 187 行附近):
   ```html
   <div class="avatar">錢</div>
   ```
   改成:
   ```html
   <div class="avatar"><img src="logo.png" alt="錢庭羽"></div>
   ```
3. 存檔。

## 2. 用 VS Code 連到 GitHub

在 VS Code 開啟這個資料夾後,打開內建終端機(選單 Terminal → New Terminal),依序執行:

```bash
git init
git add .
git commit -m "init contact page"
```

接著到 GitHub 網站建立一個新的空 repository(不要勾選 README/gitignore,保持全空),複製它給你的 remote 網址,例如:

```
https://github.com/你的帳號/contact-card.git
```

回到 VS Code 終端機:

```bash
git branch -M main
git remote add origin https://github.com/你的帳號/contact-card.git
git push -u origin main
```

之後 VS Code 左側也可以用內建的「Source Control」面板做同樣的事(不一定要打指令),但第一次建立 remote 建議用指令比較不會出錯。

## 3. 開啟 GitHub Pages

1. 到 GitHub 上這個 repo 的頁面 → **Settings** → 左側選單 **Pages**。
2. **Source** 選 `Deploy from a branch`。
3. **Branch** 選 `main`,資料夾選 `/ (root)`,按 **Save**。
4. 等 1–2 分鐘,重新整理頁面,會出現網址,格式大概是:
   ```
   https://你的帳號.github.io/contact-card/
   ```
   這就是最終聯絡頁網址。

## 4. 之後要改資料怎麼辦

直接改本機的 `index.html`,存檔後在 VS Code 終端機:

```bash
git add .
git commit -m "update info"
git push
```

網址不會變,GitHub Pages 會自動更新內容,QR code 完全不用重新產生。

## 5. 產生 QR code

拿到上面第 3 步的網址後,用任何免費 QR code 產生器(例如 [goqr.me](https://goqr.me)、[QRCode Monkey](https://www.qrcode-monkey.com))貼上網址、下載圖片即可,或跟我說一聲,我可以直接幫你生成圖檔。
