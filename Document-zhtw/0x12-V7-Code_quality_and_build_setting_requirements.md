# V7: 程式碼品質與編譯選項準則 Requirements

## 管理目標
於開發所有行動應用程式時，應採用最基本的安全程式編寫作法，並啟動編譯器內可自由使用的防衛特徵。


## 安全驗證準則

| # | 描述 | L1 | L2 |
| --- | --- | --- | --- |
| **7.1** | 行動應用程式需經過有效的憑證進行簽章與描述，並妥善的保管該簽發憑證之私鑰。| ✓ | ✓ |
| **7.2** | 行動應用程式需妥善的設定，以發佈模式編譯正式發佈版本(例如：不可偵錯)。| ✓ | ✓ |
| **7.3** | 編譯的二進位執行碼，需移除所有偵錯符號。| ✓ | ✓ |
| **7.4** | 行動應用程式除了不顯示過長的錯誤說明與偵錯訊息外，應刪除所有偵錯程式碼。| ✓ | ✓ |
| **7.5** | 所有應用於該行動應用程式的第三方資料庫與框架，皆需詳細確認來源與進行已知弱點排除。| ✓ | ✓ |
| **7.6** | 行動應用程式必須能攔截與處理各種可能的例外中斷或錯誤。| ✓ | ✓ |
| **7.7** | 以拒絕服務，為安全控制方面的預設錯誤處理邏輯。| ✓ | ✓ |
| **7.8** | 在非受控代碼中，亦須安全的調配，釋出與應用記憶體資源。| ✓ | ✓ |
| **7.9** | 啟動開發工具中可自由應用的防衛特徵，諸如 "位元組碼極簡化"，"堆疊防護"，"地址無關可執行文件(PIE)支援"，"自動引用計數(ARC)"。| ✓ | ✓ |

## 參考

OWASP 行動裝置安全測試指南，於下列的章節提供確認本章準則的詳細說明。

- Android - https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05i-Testing-Code-Quality-and-Build-Settings.md
- iOS - https://github.com/OWASP/owasp-mstg/blob/master/Document/0x06i-Testing-Code-Quality-and-Build-Settings.md

更多詳細資料，請參見:

- OWASP 十大行動裝置安全風險:  M7 - 端點程式碼品質篇
- 常見弱點列舉(CWE): https://cwe.mitre.org/data/definitions/119.html
- 常見弱點列舉(CWE): https://cwe.mitre.org/data/definitions/89.html
- 常見弱點列舉(CWE): https://cwe.mitre.org/data/definitions/388.html
- 常見弱點列舉(CWE): https://cwe.mitre.org/data/definitions/489.html
