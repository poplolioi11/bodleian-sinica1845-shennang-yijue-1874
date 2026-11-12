# 資料欄位

- document.json：沿用pages/units主本；schema為sinica1845-revised-text/2。source與modern_editor分別保存館藏與現代整理者；quality明示AI覆核範圍及未知模型資料。
- pages：id、order、官方source、bound_volume、source_frame_id、side、physical_role、source_geometry、uncertainties及適用的原印葉碼、圖版與來源層觀察。公開source metadata沿固定v0.1.0；不包含私有圖檔路徑。
- units：id、page_id、order（全書機械投影序）、native_order（原稿值，可含新增單位的分數插入序；缺省為null）、text、layer、role、review_status、bbox及原有uncertainties/gaps；保留fragments、source_segments、subcolumns、note_columns、inline_spans、parent關係與錨點。unit.source與additional_source_regions只保留原稿非私密的局部閱讀幾何；局部ROI並非全幀座標，私有圖檔不包含。order與projection_order相等，均為主本陣列中的1起算出版索引；native_order另存原稿metadata，原封存稿不改。原稿若省略uncertainties/gaps，公開層用空陣列表示沒有附掛記錄，並以native_omitted_fields記下缺省；空陣列不表示逐字確定。
- historical_initial_*與superseded_initial_anchor_fields：歷史狀態；現行uncertainties與anchor優先，不能把舊候選算作本版未解。
- text.sidecar.json：units.start/end是0起算Unicode碼位半開範圍；document_structure_without_unit_text保存除text外的完整公開結構，可與TXT精確重建主本。
- tei.sidecar.json：對應page/unit與XML IDs，另存原始text碼位長度及層；TEI中的n是原ID、type是層、corresp是既有parent的交叉參照。完整語義仍在主本。
- GAIJI.json：每次標記、unit／page、半開範圍、候選、來源與未定性；標記長度不是原印字數。
- NOTE-ANCHORS.json：所有有parent關係的單位與現行及已標名歷史錨點、跨欄片段；各原有basis不互換。
- UNRESOLVED.json：六份裁定稿選定的q狀態表，每筆保留原生status、定位與候選；包含已依原圖裁定而留存退回候選的記錄，不能把全部筆數當成未解或誤字。historical_issue_dispositions另列舊疑義處置與現行範圍對應。
- CHANGES-v0.1.0.json：全量公開單位欄位及頁metadata變更、碼位級字串編輯與前後投影ID。
- CORRECTIONS.json：本輪改字前後、公開來源與必要裁定階段理由；非完整私有事件log。
- CORRECTIONS-v0.1.0-old-initial-status.json：固定前版CORRECTIONS.json原bytes；只屬初錄時期局部補讀。
- COUNTS.json：格式與標記計數；VALIDATION.json是工程結果，不是文字準確率或專家審查。
