# 閱讀與定位

先開text.txt直接讀文字；每個unit以換行相接，這些分隔換行是匯出呈現，不是新增古籍句讀。頁、欄與文字層定位在text.sidecar.json及document.json。英文段落內原換行與斷詞保留，詞表依中英對齊行序保存，圖中文字的排列是檢索順序而非臆造連貫句子。

例如b01-f015-L為第一裝訂冊第015全幀之左語意面，b02-f060-L是第二冊正文卷四起處；R/L不是原印葉碼。document.json.pages[].source.uri是官方canvas，image_uri是當時固定1000px全幀。source.sha256固定該預覽。units[].bbox是同一全幀的[x1,y1,x2,y2]像素邊界，半面座標已平移，都是約略區域／欄定位，不是逐字偵測框。空值表示沒有可靠框；不要用預設框補出精確位置。source_geometry保存原閱讀尺寸及半面轉換。圖版語意面可能越x500，不能截成幾何半面解讀。

□表示局部尚不能可靠讀定的一印字或明記範圍，請查該頁uncertainties；未知字數與整區未處理不同。[[G...]]與⟦g-...⟧是兩份原初錄所用的穩定gaiji／來源痕跡標記，未正規化成單一字。GAIJI.json記每次出現的頁、unit、0起算Unicode碼位範圍、來源及候選；標記長度不是原印字數。

small-note是獨立小註單位；parent_unit指出主文，anchor_after_text及anchor_after_codepoint_1based指出所繫字串之後的位置。此錨點是1起算Unicode碼位，與sidecar的0起算半開範圍不同。fragments保留跨欄小註的分片及讀序，不把小註接到不相關的句末。NOTE-ANCHORS.json另列全部103個原有關係，其中90為小註。

marginal-writing、source-mark、source-damage與印正文分層。圈墨、旁改字或欄外字的責任未知，不能用旁字直接替代不可見底印。章節題、版心、印葉碼、末題、圖說、圖內標示、分圖號與英文石印署名另有layer。可見印數、原刻訛字及III/IV卷號衝突原樣保存。

CORRECTIONS.json公開同一初讀者局部回圖的前後字串／觀察及理由，沒有獨立二校或人類裁定的意義。頁uncertainties是保留的初讀疑義，須連同後續事件讀，不能僅計筆數當錯字率。TEI與TXT本身不承載全部欄位，請一併保存主本和各sidecar。

CORRECTIONS.json事件中的舊／新單位框保留初讀半面座標（500px寬，實高逐頁記錄），未假裝改字歷程的原框是全幀。document.json的正式unit框則已平移到全幀；兩種座標基準請分開讀。
