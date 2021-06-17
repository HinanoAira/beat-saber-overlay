## [The English version of the README is here.](README_EN.md)
# Beat Saber Overlay 改良版

これは、Reselim氏が製作した[Beat Saber Overlay](https://github.com/Reselim/beat-saber-overlay)に各種表示オプションを追加し、機能改善した物です。

Beat SaberをOBS等で配信や録画する時に譜面情報をオーバーレイ表示します。

![preview](https://rynan4818.github.io/beatsaber-overlay-bsr-image.png)

※画像はHttpStatusExtentionを使用したフルオプションのサンプルです。

## インストール方法 (OBS)

1. Beat Saberからオーバーレイにデータを送信するために下記のmodをインストールしてください。

   初心者はオリジナル版HTTP StatusをModAssistantからインストールすることをオススメします。ModAssistantを使用する場合は依存modが自動的にインストールされるため簡単です。

   - [Beat Saber HTTP Status](https://github.com/opl-/beatsaber-http-status)　※ModAssistant登録のオリジナル版

      ![image](https://rynan4818.github.io/beatsaber-overlay-httpstatus.png)

	ほかに、デンバ時計さん製作のパフォーマンス改善版があります。
	- [HttpSiraStatus](https://github.com/denpadokei/beatsaber-http-status)

      ![image](https://rynan4818.github.io/beatsaber-overlay-denpadokei.png)

	オプションの `pp` 機能やカスタム難易度表示を使用するには、デンバ時計さんのHttpSiraStatusとHttpStatusExtentionも導入する必要があります。
	- [HttpStatusExtention](https://github.com/denpadokei/HttpStatusExtention)

   ※手動でインストールする場合は、別途依存modをそれぞれのmodの説明に従ってインストールして下さい。
      特にModAssistantにある**websocket-sharpのインストールが必須**です。入れ忘れトラブルが多いので注意して下さい。

   ![image](https://rynan4818.github.io/beatsaber-overlay-websocket-sharp.png)

2. [リリースページ](https://github.com/rynan4818/beat-saber-overlay/releases)から最新のリリースをダウンロードします。

3. ダウンロードしたzipファイルを適当なフォルダに解凍します。(例: C:\TOOL\beat-saber-overlay)

4. OBSのソースにブラウザを追加します。

   ![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting1.png)

5. 新規作成を選択して、適当にソースの名前を設定して、OKを押します。

   ![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting2.png)

6. 解凍したzipファイルの中にある、index.html をダブルクリックするか、ChromeやEdgeブラウザで開きます。

   ![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting3.png)

7. ブラウザのアドレス(URL)欄を選択してコピーします。

   ![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting4.png)

8. コピーしたアドレスを、OBSのURL欄に貼り付けます。

   ![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting5.png)

   ※`ローカルファイル`だと、オプション設定が出来ないのでこの様にURL表記で入力する必要があります。
  
   ※画面サイズに合わせてサイズを設定します。(1280x720等)
  
   ※(オプション) 1080p(1920x1080)の画面サイズの場合、オーバレイ表示を1.5倍に拡大する `scale` 修飾子を使用して下さい。

         file:///C:/TOOL/beat-saber-overlay/index.html?modifiers=scale

9. 必要に応じて URLのindex.htmlの後に `?modifiers=` を追加してオプションを設定します。複数のオプションはカンマ(,)で区切ります。

   ![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting6.png)

10. プロパティの幅は意図的に縮めることで、オーバーレイの表示幅を絞ることが可能です。

    曲名、アーティスト・作譜者、難易度(カスタム難易度）が幅を超える場合に自動でスクロールします。

    ![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting7.png)

    ![image](https://rynan4818.github.io/beatsaber-overlay-scllol.gif)

11. オーバーレイのソースの順序をゲームのソースよりも優先度を上げて、オーバーレイがゲーム画面に重ねて表示されるようにします。

    ![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting8.png)

## オプション

次の様なオプションがURLに設定可能です。

```
file:///C:/TOOL/beat-saber-overlay/index.html?modifiers=top,all
```

### `modifiers`

複数のオプションは,(カンマ)で区切ることができます。

- `top`
	* オーバーレイの表示を上部に配置し、レイアウトを垂直方向に反転します。
- `rtl`
	* オーバーレイを右に移動し、右揃えのレイアウトにします。
- `scale`
	* 1080p(1920x1080)の画面で使用するために、オーバーレイを1.5倍にスケーリングします。
- `test`
	* テストのために背景を黒にします。
- `bsr`
	* bsrの検索・表示をします。
- `miss`
	* ミス数を表示します。
- `mod`
	* Modifierを表示します。(DA,FS等)
- `energy`
	* エナジーバーを表示します
- `pp`
	* ランク譜面の時に精度100%のpp値、Star Difficulty、リアルタイムのpp値を表示します。（※１）
- `label`
	* カスタム難易度がある場合に、デフォルトの難易度と共に表示します。（※１）
- `all`
	* `bsr`, `miss`, `mod`, `energy`, `pp`, `label` オプションを全て表示します。（※１）
- `no-performance`
	* スコア表示を消します。
- `no-hidden`
	* 終了時に表示を消しません。

※１：`pp`, `label` オプションを表示するには、[HttpStatusExtention](https://github.com/denpadokei/HttpStatusExtention)の導入が必要です。

### `ip`または`port`

ゲームとOBSが別のPCの場合に、ゲーム用PCのBeat Saber HTTP Statusに接続する場合に設定します。

オプションは省略すると、ip=localhost 及び port=6557 となります。
```
file:///C:/TOOL/beat-saber-overlay/index.html?ip=192.168.1.10&port=6557&modifiers=top,bsr
```

## 機能追加、表示変更スキン
オーバーレイに機能追加、表示変更する追加スクリプト、ＣＳＳがあります。

- [BSDP-Overlayライクなオーバーレイ](https://github.com/rynan4818/bsdp-like-overlay) オーバーレイ改造のサンプル
- [OBS Studioで自動シーン切り替え](https://github.com/rynan4818/obs-control)
- [Streamlabs OBSで自動シーン切り替え](https://github.com/rynan4818/Streamlabs-obs-control)
- [タイトル表示変更、エナジーバーの色変化スキン](https://twitter.com/NullponVR/status/1376585288500191234) ぬるぽんさん製作

※[XSplit Broadcasterの自動シーン切り替え](https://github.com/rynan4818/BS-AutoSceneChanger) (オーバーレイとは関係ありません)

# オーバーレイが動作しない場合
[トラブルシューティング](Troubleshooting.md)を確認してください。

# オーバーレイの改造について
オーバーレイは改造し易くするため、いくつか機能が用意されています。

## HTMLの書き換え対象のid属性の有無チェック
オーバーレイのスクリプトでは特定のid属性値のHTMLタグに対して、プレイに合わせた書き換え動作をします。

HTML内のid属性値は起動時にチェックし、存在しない場合は書き換え動作をしないため、HTMLやCSSを改造して好きなレイアウトや表示項目にすることが出来ます。

初心者向けに改造方法の記事を書きました。 [HTMLを知らない人にも分かる、オーバーレイの改造の仕方を説明してみる](https://note.com/rynan/n/n9a4207b7aed5)

参考に、精度・スコア・曲名・bsr表示だけにしたシンプルな表示のhtmlを用意してあります。
```
file:///C:/TOOL/beat-saber-overlay/simple.html?modifiers=bsr
```

| id属性値 | 動作 |
----|----
| overlay | プレイ開始時にclass="hidden"を削除、終了時に付与します。 |
| rank | スコアのランク(SS,S,A,B,C・・・)に書き換えます。 |
| percentage | スコアの精度(xx.x%)に書き換えます。 |
| combo | コンボ数に書き換えます。 |
| score | スコアに書き換えます。 |
| progress | 曲のプレイ時間に応じたstroke-dashoffsetスタイル値(半径30pxの円周値px)を設定します。 |
| image | src属性に曲のカバー画像をセットします。 |
| title | 曲のタイトルに書き換えます。 |
| subtitle | 曲のサブタイトル情報に書き換えます。 |
| artist | 曲のアーティスト情報に書き換えます。 |
| difficulty | 難易度情報に書き換えます。 |
| bpm | 曲のBPM情報に書き換えます。 |
| njs | NJS情報に書き換えます。 |
| njs_text | NJSの項目名を起動時に保持し、NJS表示が出来ない場合は表示を消します。 |
| bsr | BeatSaverのkey(bsr)情報に書き換えます。 |
| bsr_text | bsrの項目名を起動時に保持し、bsr表示が出来ない場合は表示を消します。 |
| mapper | 譜面の作者名を表示します。 |
| mapper_header | 譜面の作者名のヘッダー表示を起動時に保持し、表示出来ない場合は消します。 |
| mapper_footer | 譜面の作者名のフッター表示を起動時に保持し、表示出来ない場合は消します。 |
| song_time | プレイ中の曲の再生時間に書き換えます。 |
| song_length | 曲の長さの時間に書き換えます。 |
| mod | 適用中のmod(IF,BE,DA,GN,FS,SS,NF,NO,NB,NA)情報に書き換えます。 |
| miss | ミス数(ノーツミス)に書き換えます。 |
| pre_bsr | 一つ前にプレイした譜面のbsr情報を表示します。 |
| pre_bsr_text | pre_bsrの項目名を起動時に保持し、NJS表示が出来ない場合は表示を消します。　|
| energy | ライフ値(xxx%)に書き換えます。 |
| energy_bar | ライフ値に応じたwidthスタイル値(xxx%)を設定ます。 |
| energy_group | No Fail時にvisibilityスタイルをhiddenにします。 |
| now_pp | 現在のpp値に書き換えます。 |
| now_pp_text | now_ppの項目名を起動時に保持し、now_pp表示が出来ない場合は表示を消します。 |
| star | Star Difficulty値に書き換えます。 |
| star_text | starの項目名を起動時に保持し、star表示が出来ない場合は表示を消します。 |
| pp | 精度100%のpp値に書き換えます。 |
| pp_text | ppの項目名を起動時に保持し、pp表示が出来ない場合は表示を消します。 |

## modifiersオプションの追加
modifiersフォルダにCSSファイルを追加すると、CSSファイル名でmodifiersオプションを指定して読み込める様になります。
独自スタイルのCSSを作成した場合に任意のCSSファイルを作成することで、オリジナルのOverlayのファイル群を直接改造する必要がなくなるため、アップデートに追従しやすくなったり、他人に配布が容易になります。

## 外部スクリプト起動用オプション配列
スコアに応じて色を変更するなど、動的にオーバーレイを変化させるにはJavascriptを作成する必要があります。

オリジナルのJSコードに手を付けなくても以下のオプション配列の要素として関数を追加すると。各イベントで呼び出されます。

なお、追加するスクリプトは最初(options.jsより前、startup.jsより後)に読み込んで下さい。

| 配列 | (引数) | 説明 |
----|----|----
| ex_performance | (data,now_energy) | performanceが更新されるタイミングで呼び出されます |
| ex_timer_update | (time, delta, progress, percentage) | 曲時間表示が更新されるタイミングで呼び出されます |
| ex_timer_update_sec | (time, delta, progress, percentage) | 曲時間表示(秒毎)が更新されるタイミングで呼び出されます |
| ex_beatmap | (data,now_map,pre_map) | 譜面情報が更新されるタイミングで呼び出されます |
| ex_beatsaver_res | (now_map) | BeatSaverの譜面情報問い合わせのレスポンスがあった場合に呼び出されます |
| ex_hide | () | オーバーレイを隠すタイミングで呼び出されます |
| ex_show | () | オーバーレイを表示するタイミングで呼び出されます |
| ex_hello | (data) | HTTP Status の hello イベント時に呼び出されます |
| ex_songStart | (data) | HTTP Status の songStart イベント時に呼び出されます |
| ex_noteCut | (data) | HTTP Status の noteCut イベント時に呼び出されます |
| ex_noteFullyCut | (data) | HTTP Status の noteFullyCut イベント時に呼び出されます |
| ex_obstacleEnter | (data) | HTTP Status の obstacleEnter イベント時に呼び出されます |
| ex_obstacleExit | (data) | HTTP Status の obstacleExit イベント時に呼び出されます |
| ex_noteMissed | (data) | HTTP Status の noteMissed イベント時に呼び出されます |
| ex_bombCut | (data) | HTTP Status の bombCut イベント時に呼び出されます |
| ex_finished | (data) | HTTP Status の finished イベント時に呼び出されます |
| ex_failed | (data) | HTTP Status の failed イベント時に呼び出されます |
| ex_softFailed | (data) | HTTP Status の softFailed イベント時に呼び出されます |
| ex_scoreChanged | (data) | HTTP Status の scoreChanged イベント時に呼び出されます |
| ex_energyChanged | (data) | HTTP Status の energyChanged イベント時に呼び出されます(本家HTTPStatusは未実装) |
| ex_pause | (data) | HTTP Status の pause イベント時に呼び出されます |
| ex_resume | (data) | HTTP Status の resume イベント時に呼び出されます |
| ex_menu | (data) | HTTP Status の menu イベント時に呼び出されます |

| 引数 | 説明 |
----|----
| data | HTTP Status から送信される[JSONオブジェクト](https://github.com/opl-/beatsaber-http-status/blob/master/protocol.md)が格納されています |
| now_energy | ライフ値が格納されています(0～100 実数値[小数点有り]) |
| delta | 曲の経過時間(msec) |
| progress | 曲の経過時間(sec) |
| percentage | 曲の経過割合 |
| now_map | 現在の譜面のBeatSaver API 問い合わせ結果の[JSONオブジェクト](https://beatsaver.com/api/maps/by-hash/071048B302300C07788D8422D05F7CCDF457FE40)。但し、op_beatmapの時は前回と同じ譜面のプレイ時のみ格納、それ以外はnull |
| pre_map | 前回の譜面のBeatSaver API 問い合わせ結果のJSONオブジェクト。 |

### ランクの色分け表示サンプル
参考として、ランク表示をCounters+の様にSSは水色、Aは黄緑、Bは黄色、Cは橙、DEは赤にする例を示します。

下記のコードをindex.htmlの`<script src="./js/options.js"></script>`の上の行に挿入して下さい。

	<script type="text/javascript">
	ex_performance.push((data,now_energy) => {
	    let rank = document.getElementById("rank");
	    switch (data.status.performance.rank) {
	        case "SSS":
	        case "SS":
	            rank.style.color = "cyan";
	            break;
	        case "S":
	            rank.style.color = "white";
	            break;
	        case "A":
	            rank.style.color = "lime";
	            break;
	        case "B":
	            rank.style.color = "yellow";
	            break;
	        case "C":
	            rank.style.color = "orange";
	            break;
	        case "D":
	        case "E":
	            rank.style.color = "red";
	    }
	});
	</script>

[Release v2021/02/22](https://github.com/rynan4818/beat-saber-overlay/tree/12c8cafa54663e6aec81bde5e1db008000e3444a#%E5%A4%96%E9%83%A8%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%97%E3%83%88%E8%B5%B7%E5%8B%95%E7%94%A8%E3%82%AA%E3%83%97%E3%82%B7%E3%83%A7%E3%83%B3%E9%96%A2%E6%95%B0)以前のオプション関数(op_*)も互換性維持のため読み込むようになっています。

ただし、オプション関数はスクリプト全体で１箇所しか使用できないため、他のスクリプトと競合する場合は関数を合成する必要があります。

オプション配列の場合は、そういった問題はありませんので今後は配列に関数を追加して使用して下さい。

# その他

他のオーバーレイでは一般的なGitHub Pages等による本オーバーレイの提供は以下を理由にあえて行いません。

- オリジナルの(Unnamed) Beat Saber OverlayではURL変更等によるトラブルが多かったこと
- GitHubに繋がらない場合など、ネットワークのトラブル時に使用できないこと
- 少し手間になるが、ダウンロードしてローカルで表示する使用方法で問題ないこと
