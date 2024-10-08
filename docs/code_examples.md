# Code Examples

[RICOH Viewer Local Sample Code guide in Japanese](https://www.notion.so/ricoh360/2024-08-28-Swift-06dff572af57443b859a4d760c267195)

- 表示用のhtmlとplatformから提供されたjsをアプリ内に梱包しておく
- 上記htmlとjsおよびローカルの画像が同じフォルダ内にある状態でviewerに読み込ませるとローカルの画像を再生できる

## local viewer code

![local files](images/local_files.png)

## index.html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta name="viewport" content="width=device-width, user-scalable=no" />
    <title>PF Viewer DEMO</title>
  </head>
  <body>
    <div
      style="
             position: relative;
             width: 100%;
             height: 400px;
             background-color: #2a303c;
            "
            >
            <div id="viewer" style="width:300px; height:150px;"></div>
            <div id="message" style="width:300px; height:150px;"></div>
    </div>
    <!--  RICOH360 Platformから提供されているviewerのjavascriptを読み込み  -->
    <script src="./ricoh360-viewer.js"></script>
    <script>
      // 初回の画像読み込みか、2枚目以降の読み込みかを判定するフラグ
      started = false;
      
      // Platform上の画像を取得する際の認証に利用するトークンを返す関数
      // 本サンプルはローカルの画像を表示するためトークンは必要ないが、関数自体は初期化の際に必要なため空文字を返す関数を定義
      const onFetchToken = async()=>{
        return ""
      };
      
      // viewerの初期化
      // この時点では表示位置にviewerが生成され黒背景のエリアが表示される
      viewer = new RICOH360Viewer({
        divId: 'viewer',
        onFetchToken,
      });
      
      // 初回の画像読み込みはstart関数を利用し、それ以降はswitchScene関数でviewerに画像を表示する
      const show = (filePath) => {
        if(started){
          viewer.switchScene({filePath});
        }else{
          viewer.start({filePath});
          started = true;
        }
      }
    </script>
  </body>
</html>
```
