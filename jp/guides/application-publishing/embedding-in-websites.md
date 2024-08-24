# ウェブサイトへの埋め込み

Mlchain Apps は iframe を使用してウェブサイトに埋め込むことができます。これにより、Mlchain App をウェブサイト、ブログ、またはその他のウェブページに統合できます。

Mlchain Chatbot Bubble Button をウェブサイトに埋め込む際に、ボタンのスタイル、位置、その他の設定をカスタマイズできます。

## Mlchain Chatbot Bubble Button のカスタマイズ

Mlchain Chatbot Bubble Button は、以下の設定オプションでカスタマイズできます。

```javascript
window.mlchainChatbotConfig = {
    // 必須：Mlchain によって自動的に生成されます
    token: 'YOUR_TOKEN',
    // オプション：デフォルトは false です
    isDev: false,
    // オプション：isDev が true の場合、デフォルトは '[https://dev.umlchain.app](https://dev.umlchain.app)'、それ以外の場合は '[https://umlchain.app](https://umlchain.app)' です
    baseUrl: 'YOUR_BASE_URL',
    // オプション：`id` 以外の有効な HTMLElement 属性（例：`style`、`className` など）を受け入れます
    containerProps: {},
    // オプション：ボタンのドラッグを許可するかどうか、デフォルトは `false` です
    draggable: false,
    // オプション：ボタンのドラッグを許可する軸、デフォルトは 'both'、'x'、'y'、'both' のいずれかを指定できます
    dragAxis: 'both',
    // オプション:mlchain チャットボットに設定されている入力オブジェクト
    inputs: {
        // key は変数名です
        // 例:
        // name: "NAME"
    }
};
```

## デフォルトのボタンスタイルの上書き

CSS 変数または `containerProps` オプションを使用して、デフォルトのボタンスタイルを上書きできます。CSSの優先度に基づいてこれらの方法を適用し、希望のカスタマイズを実現します。

### 1.CSS 変数の変更

以下の CSS 変数をカスタマイズに使用できます。

```css
/* ボタンの下端からの距離、デフォルトは `1rem` */
--mlchain-chatbot-bubble-button-bottom

/* ボタンの右端からの距離、デフォルトは `1rem` */
--mlchain-chatbot-bubble-button-right

/* ボタンの左端からの距離、デフォルトは `unset` */
--mlchain-chatbot-bubble-button-left

/* ボタンの上端からの距離、デフォルトは `unset` */
--mlchain-chatbot-bubble-button-top

/* ボタンの背景色、デフォルトは `#155EEF` */
--mlchain-chatbot-bubble-button-bg-color

/* ボタンの幅、デフォルトは `50px` */
--mlchain-chatbot-bubble-button-width

/* ボタンの高さ、デフォルトは `50px` */
--mlchain-chatbot-bubble-button-height

/* ボタンの角丸、デフォルトは `25px` */
--mlchain-chatbot-bubble-button-border-radius

/* ボタンのボックスシャドウ、デフォルトは `rgba(0, 0, 0, 0.2) 0px 4px 8px 0px)` */
--mlchain-chatbot-bubble-button-box-shadow

/* ボタンホバー時の変形、デフォルトは `scale(1.1)` */
--mlchain-chatbot-bubble-button-hover-transform
```

例えば、ボタンの背景色を #ABCDEF に変更するには、次の CSS を追加します。

```css
#mlchain-chatbot-bubble-button {
    --mlchain-chatbot-bubble-button-bg-color: #ABCDEF;
}
```

### 2.`containerProps` を使用する

`style` 属性を使用してインラインスタイルを設定します。

```javascript
window.mlchainChatbotConfig = {
    // ... 他の設定
    containerProps: {
        style: {
            backgroundColor: '#ABCDEF',
            width: '60px',
            height: '60px',
            borderRadius: '30px',
        },
        // ちょっとしたスタイル変更の場合、style 属性に文字列を使用することもできます。
        // style: 'background-color: #ABCDEF; width: 60px;',
    },
};
```

`className` 属性を使用して CSS クラスを適用します。

### 3. `inputs` の渡し方

サポートされている入力タイプは4種類あります：

1. **`text-input`**：任意の値を受け入れます。入力文字列の長さが許容される最大長を超える場合、切り詰められます。
2. **`paragraph`**：`text-input` と同様に、任意の値を受け入れ、文字列が最大長を超える場合には切り詰められます。
3. **`number`**：数値または数値の文字列を受け入れます。文字列が提供された場合、`Number` 関数を使用して数値に変換されます。
4. **`options`**：事前に設定されたオプションのいずれかと一致する値を受け入れます。

設定例：

```javascript
window.mlchainChatbotConfig = {
    // 他の設定項目...
    inputs: {
        name: 'apple',
    },
}
```

注意: `embed.js` スクリプトを使用してiframeを作成する場合、各入力値はURLに追加される前にGZIPで圧縮され、base64でエンコードされます。

例えば、処理された入力値を含むURLは以下のようになります：
`http://localhost/chatbot/{token}?name=H4sIAKUlmWYA%2FwWAIQ0AAACDsl7gLuiv2PQEUNAuqQUAAAA%3D`