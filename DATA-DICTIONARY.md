# 資料欄位

- document.json：schema、id、title、version、source、publication_status、quality、pages、units；品質僅initial。modern_editor為現代整理者；METADATA.json另列historical_responsibility。
- pages：id、order、source（uri/image_uri/sha256/width/height）、bound_volume、source_frame_id、side、physical_role、source_geometry、uncertainties與原有附記。
- units：id、page_id、order、text、layer、role、review_status、bbox、uncertainties、gaps；保留原reading_order、typographic_spans、fragments、parent_unit及錨點等適用欄位。bbox_mapping解釋座標轉換；未新增逐字框。
- text.sidecar.json：units的start/end為0起算Unicode碼位半開範圍，separator為匯出換行。不是UTF-8位元組或UTF-16單元。
- tei.sidecar.json：page/unit ID與TEI產生的XML ID對照；text.tei.xml中的type保留layer、n保留unit ID，corresp僅對應已有parent。
- GAIJI.json：每次穩定標記及候選、頁／unit／來源；不同形狀的標記不自動視同一字。
- NOTE-ANCHORS.json：103個主文關係；其中90 small-note，13其他原有關係。錨點1起算基準另標。
- CORRECTIONS.json：同一初讀者具來源局部補讀事件，包含保持未解及結構修正；不是獨立校勘表。
- COUNTS.json：固定規則計數，碼位不是原印字數；units含正文、版心、圖中文字及來源痕跡。
- METADATA.json：中英文摘要、來源、Methods、分層權利、keywords與品質。DOI與repository尚未發布時為null。

來源文字不做Unicode正規化、簡繁轉換、異體合併、現代醫名替代或數字校正。空值與空列按原語義保留，不推成零或無疑義。完整書別原始資料及私有證據不在公開包；本主本保留讀者解讀所需的原文字串與結構。
