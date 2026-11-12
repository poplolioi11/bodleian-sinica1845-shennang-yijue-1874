# 閱讀與定位

text.txt依主本units陣列逐單位輸出，以換行分隔；分隔符是匯出呈現，不是原刻句讀。小註、後加手寫、版心、圖中文字和來源墨跡另列，不能把相鄰輸出當作連讀校訂正文。原單位內換行、碼位、異體及標記保持不變。

page ID如b01-f015-L表示第一裝訂冊第015來源全幀的左語意面，R/L不是印葉碼。pages[].source.uri是官方canvas，image_uri是固定1000px全幀；SHA固定預覽來源。三冊I / II+IV / III的裝訂次序及卷號衝突保留。

units[].bbox是全幀預覽[x1,y1,x2,y2]邊界，通常只是手工約略欄／區域定位。首60面小註另有bbox_in_face_xywh，表示原閱讀半面內的約略子欄；它與沿用的whole-frame bbox用途和精度不同，不能假設逐點等同。source_geometry保留半面轉換與閱讀尺寸；無可靠框為null，不是空白或精確座標。fragments、source_segments與subcolumns保留跨欄／雙行小註的原片段與讀序，不能任意接到另一主欄。圖字的語意面可跨幾何半面。

NOTE-ANCHORS.json同時保留native的anchor、parent_anchor、parent_unit、parent_unit_id及相關欄位。parent_anchor以start/end表示父字串的半開範圍，起終相同則為插入邊界；parent_anchor_text若有，須與該範圍原字串一致。anchor.offset與parent_offset依明示basis是Unicode碼位邊界；anchor_after_codepoint_1based是原有名稱，值表示所繫字串之後的邊界。不得用物理印字數代替包含gaiji標記字串的碼位數。superseded_initial_anchor_fields是已被現行anchor取代的舊欄位，不能作有效錨點。

GAIJI.json逐次記⟦g-…⟧、⟦mark-…⟧、⟦來源位置ID⟧、[[G…]]及本版明確登錄的〓覆墨未定字位置之原字串及0起算半開範圍。□及未知範圍依UNRESOLVED.json和主本uncertainties判讀；不把整區尚未處理偽裝成一字缺口。不同標記不自動視同一字，候選不自動替正文。b03-f024-R/f034-R未定葉碼及f063圖形方向標記維持原有未定語義。

CHANGES-v0.1.0.json完整列相對前版公開欄位差異；CORRECTIONS.json是本輪改字摘要；CORRECTIONS-v0.1.0-old-initial-status.json只屬前版初錄歷史。q記錄的status分別保存未解讀法、碼位／字形關係未定、已回圖裁定而留存退回候選、來源圖形等狀態；不能把全部q當作仍未解或錯字。後墨不能自動替原刻。TEI為交換投影，請連同document.json及sidecars保存全部語義。RECONSTRUCTION.md說明僅用公開檔案恢復主本的方法。
