# Mediawiki APIとSPARQLによって文章をアノテーションするアプリ
### [アプリ実行](https://masapi61.github.io/Annotation-by-Wikidata/index.html)  
　キーワードから[wikidata](https://www.wikidata.org/wiki/Wikidata:%E3%83%A1%E3%82%A4%E3%83%B3%E3%83%9A%E3%83%BC%E3%82%B8)を通してそのキーワードの情報を正確に得ること。また、それに関連した情報を得ることを目的にして開発したアプリケーションになります。仕組みはMediawiki APIのWikidataラベル検索API、[前方一致検索API](https://www.wikidata.org/w/api.php?action=help&modules=wbsearchentities)と[あいまい検索API](https://www.mediawiki.org/w/api.php?action=help&modules=query%2Bsearch)にkuromoji.jsで形態素解析を行い抽出した名詞を入力して検索し、そのラベル検索APIから得たwikidataのidを次はSPARQLに問い合わせてカテゴリーなどの情報を得ています。APIとSPARQLを繰り返し利用する性質上、処理時間がとても長くなっていることが欠点です。
 
# 使い方  
* 真ん中のテキストエリアにアノテーションしたい文章を入力して下さい。そしてアノテーション実行ボタンをクリックするとアノテーションが実行されます。  
* 例文ボタンのどれかを押して頂くとテキストエリアに例文が挿入されます。
* 左のカテゴリーをクリックすると文章中の選択されたカテゴリーに該当する単語がカテゴリーに対応した色にハイライトされアノテーションされます。カテゴリーに該当していない単語は普通にアノテーションされます。
* 詳細設定の説明です。詳細設定をクリックすると折りたたまれていた詳細設定が表示されます。
  * 一番上のラベル検索設定は、「完全一致」「前方一致」「あいまい検索」が選択できるようになっていて、デフォルトは完全一致となっています。この設定は上記の前方一致検索APIかあいまい検索APIのどちらを利用するかという設定になります。完全一致検索は前方一致検索の結果を使用して、プログラムの部分ででフィルタリングを行っています。アノテーションされているリンクがうまくいっていない場合は設定を切り替えて試してみて下さい。
  * 品詞の選択は、形態素解析で分析される品詞の種類でどの品詞をアノテーションの対象にするか選択することができます。デフォルトは名詞ホワイトリストとなっています。
    * 「固有名詞のみ」は固有名詞に分類される単語をアノテーションします。
    * 「名詞のみ」は名詞に分類されるものをアノテーションします。
    * 「名詞ホワイトリスト」は名詞に分類される単語からさらに分類される固有名詞、一般、数、代名詞などテキストエリアに入力した分類のアノテーションを許可します。(使用される方はブラウザのコンソールに「形態素解析結果」を出力していますのでそこのposの欄を見ていただけるとどの単語が何に分類されているのか表示されています。)
    * 「名詞ブラックリストは」逆にテキストエリア入力した分類のアノテーションを禁止します。　
*　NGワード設定は入力した文字のアノテーションを禁止する設定です。文字は「 , 」で区切って指定してください。例としてNGワードに「Wikidata」と「ナレッジグラフ」を指定したい場合は　Wikidata,ナレッジグラフ　と入力してください。

# 改善予定
* カテゴリーの追加　1層目、2層目、3層目のカテゴリーを追加しようと考えています。
* レイアウトの調整　cssなど全然使えていないので勉強し、改善できればと考えています。
