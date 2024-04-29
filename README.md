# kkcat-ip｜一個 IP 信息查詢網頁
示範網站：https://ip.kkcat.blog/

示範網站：https://kkcat-ip.pages.dev

![](https://raw.githubusercontent.com/KKKKKCAT/kkcat-ip/main/kkcat-ip.png)

### 功能和設計
這個網頁的主要功能是展示訪問者的公共 IP 信息，包括網絡、城市、國家、大陸、時區及其地理坐標。此外，網頁還能顯示與特定 Telegram 數據中心的連接狀態，包括它們的響應時間和當前狀態（通過顏色指示燈顯示）。

### 主要特點包括：

- 用戶界面：網頁使用流暢的漸變背景和中性色調的設計元素，營造出清新而現代的視覺效果。整個界面布局簡潔，所有信息都被優雅地組織並易於讀取。
- 實時數據獲取：通過異步 JavaScript 請求，網頁實時從公開的 API 獲取 IP 數據和 Telegram 數據中心的狀態。
- 狀態指示燈：每個數據中心旁邊有一個狀態燈，根據數據中心的狀態顯示不同的顏色。綠色代表一切正常，紅色則表示有問題。此外，這些狀態燈還會有閃爍效果，以引起用戶的注意。
- 響應式設計：網頁能夠適應不同大小的屏幕，確保在手機、平板和桌面計算機上都能提供良好的用戶體驗。

### 技術實現
網頁後端采用了異步 JavaScript（AJAX）來處理數據的獲取和展示。使用 fetch API 從不同的源異步獲取數據，然後將結果動態顯示在頁面上。例如，通過以下代碼片段獲取 IP 信息：
```
async function fetchIPInfo() {
    try {
        const response = await fetch('https://ipapi.co/json/');
        const data = await response.json();
        const info = `IP: ${data.ip}
        Network: ${data.network}
        City: ${data.city}
        Country: ${data.country_name} (${data.country_code})
        Continent: ${data.continent_code}
        Time Zone: ${data.timezone} (UTC Offset: ${data.utc_offset})
        Latitude: ${data.latitude}
        Longitude: ${data.longitude}
        ASN: ${data.asn}
        Organization: ${data.org}`;
        document.getElementById('ipInfo').innerText = info;
    } catch (error) {
        document.getElementById('ipInfo').innerText = 'Unable to fetch IP information. Please check your network settings or try again later.';
    }
}

```

### 部署
Cloudflare Pages / 自行upload index.html
