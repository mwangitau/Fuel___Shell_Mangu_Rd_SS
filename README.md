# ⚡ Kiryan Energy Ltd - Mangu Shell Service Station Dashboards

![Dashboard Preview](https://img.shields.io/badge/Status-Active-success)
![License](https://img.shields.io/badge/License-Proprietary-red)
![Version](https://img.shields.io/badge/Version-2.1-blue)

**Comprehensive performance analytics dashboards for Shell Mangu Road Service Station operations in Kenya.**

---

## 📊 Overview

This repository contains interactive web-based dashboards for monitoring and analyzing key operational metrics at Kiryan Energy Ltd's Shell Mangu Road Service Station. The dashboards provide real-time insights into fuel sales, staff performance, product inventory, and gas operations.

## 🎯 Features

### Dashboard Suite

1. **⛽ Fuel Per Pump Analysis**
   - Real-time pump performance tracking
   - Efficiency metrics per pump station
   - Sales trends and variance analysis
   - Date range filtering and comparison

2. **👥 Staff Management Dashboard**
   - Staff shortage tracking
   - Daily balance monitoring
   - Performance metrics
   - Multi-month data comparison

3. **📊 Product Analysis Dashboard**
   - Inventory management
   - Variance tracking (Dip Sale vs Meter Sale)
   - Stock level alerts
   - Product-wise sales comparison
   - Delivery analysis

4. **🔥 Gas Operations Dashboard**
   - Cylinder sales tracking (6KG, 13KG, 25KG, 45KG)
   - Pieces to kilograms conversion
   - Daily sales trends
   - Product distribution analysis

## 🚀 Quick Start

### Prerequisites

- Modern web browser (Chrome, Firefox, Safari, Edge)
- Internet connection (for Chart.js CDN)
- Google Sheets account (for data integration)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/Fuel___Shell_Mangu_Rd_SS.git
   cd Fuel___Shell_Mangu_Rd_SS
   ```

2. **Open the dashboards**
   - Open `index.html` in your web browser
   - Or deploy to GitHub Pages (see Deployment section)

### Local Setup

Simply open `index.html` in any modern web browser. All dashboards are client-side only and require no server setup.

## 📁 Project Structure

```
Fuel___Shell_Mangu_Rd_SS/
├── index.html                          # Main landing page
├── staff_dashboard.html                # Staff management dashboard
├── fuel/
│   └── fuel_dashboard_easy_config.html # Fuel pump analysis
├── Product/
│   └── product_dashboard.html          # Product inventory & variance
└── Gas/
    └── gas_dashboard_pivot_format.html # Gas operations tracking
```

## ⚙️ Configuration

### Adding New Month Data

Each dashboard reads data from Google Sheets via published CSV links. To add a new month:

1. **Prepare your Google Sheet** with the correct format
2. **Publish to web**: File → Share → Publish to web
3. **Select CSV format** for the specific sheet/tab
4. **Copy the published CSV link**
5. **Edit the dashboard HTML file** and add your month:

```javascript
const dataSources = {
  "December": "YOUR_CSV_LINK_HERE",
  "November": "...",
  "October": "..."
};
```

6. **Save and refresh** - the new month appears automatically!

### Data Format Requirements

#### Fuel Dashboard
Required columns: `DATE`, `PUMP`, `PRODUCT`, `OPENING`, `SALES`, `CLOSING`, `PRICE`

#### Staff Dashboard
Required columns: `DAY`, `[Staff Member Names...]`

#### Product Dashboard
Required columns: `DATE`, `PRODUCT`, `OPEN DIP`, `DELIVERY`, `CLOSE DIP`, `DIP SALE`, `METER SALE`, `VAR`, `EXPLAIN > 5%`

#### Gas Dashboard
Format: Pivot table with products in rows, dates in columns
- Row 1: Dates (2025.11.01, 2025.11.02, etc.)
- Column A: Product names (6KG REFILL, 13KG EMPTY, etc.)
- Data cells: Pieces sold

## 🎨 Customization

### Product Colors

Edit the `PRODUCT_COLORS` object in each dashboard:

```javascript
const PRODUCT_COLORS = {
  'DX': '#000000',  // Black - Diesel
  'UX': '#10b981',  // Green - Unleaded Super
  'VP': '#dc2626'   // Red - V-Power
};
```

### Date Format

Dashboards support both formats:
- `YYYY.MM.DD` (2025.11.28)
- `DD.MM.YYYY` (28.11.2025)

## 🌐 Deployment

### GitHub Pages

1. **Push to GitHub**
   ```bash
   git add .
   git commit -m "Initial commit"
   git push origin main
   ```

2. **Enable GitHub Pages**
   - Go to repository Settings
   - Navigate to Pages section
   - Source: Deploy from branch `main`
   - Folder: `/ (root)`
   - Save

3. **Access your site**
   - URL: `https://yourusername.github.io/Fuel___Shell_Mangu_Rd_SS/`

### Alternative Hosting

- **Netlify**: Drag and drop the entire folder
- **Vercel**: Connect GitHub repository
- **Local Server**: `python -m http.server 8000`

## 📱 Browser Compatibility

- ✅ Chrome/Edge (recommended)
- ✅ Firefox
- ✅ Safari
- ✅ Mobile browsers (responsive design)

## 🔒 Security & Confidentiality

**⚠️ IMPORTANT NOTICE**

These dashboards contain **sensitive business data** and are for **official use only**.

- Unauthorized access is prohibited
- Do not share CSV links publicly
- Consider password-protecting your GitHub repository
- Use private repositories for production data

## 🛠️ Technologies Used

- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **Charts**: Chart.js 3.9.1
- **Data Source**: Google Sheets (CSV export)
- **Styling**: Custom CSS with glassmorphism effects
- **Icons**: Unicode emoji icons

## 📈 Key Metrics

### System Performance
- ⚡ **99% Uptime**
- 📊 **4 Active Dashboards**
- 🔢 **5,738.56 Avg. Litres/Day**

### Dashboard Features
- 📅 Multi-month data support
- 🔄 Real-time updates
- 📊 Interactive charts
- 🔍 Advanced filtering
- 📱 Mobile responsive
- 🎨 Dark/light themes

## 🤝 Contributing

This is a private business tool. Internal contributions:

1. Test changes locally first
2. Update documentation
3. Follow existing code style
4. Create descriptive commit messages

## 📝 Version History

### v2.1 (Current)
- ✅ Removed configuration helper boxes
- ✅ Fixed pivot table format for Gas dashboard
- ✅ Added pieces-to-KG conversion
- ✅ Updated date format handling
- ✅ Improved mobile responsiveness

### v2.0
- Multi-month data support
- Easy CSV configuration
- Custom product colors
- Enhanced visualizations

### v1.0
- Initial dashboard release
- Basic reporting features

## 📞 Support

For technical support or questions:
- **Email**: [mwangijohngitau1@gmail.com]
- **Manager**: [manager - +254717034328]
- **Station**: Shell Mangu Road Service Station, Kenya

## 📄 License

**Proprietary & Confidential**

© 2025 Kiryan Energy Ltd — All Rights Reserved

This software and associated documentation are proprietary to Kiryan Energy Ltd. Unauthorized copying, distribution, or use is strictly prohibited.

---

## 🙏 Acknowledgments

Built with dedication for operational excellence at Shell Mangu Road Service Station.

**Maintained by**: Kiryan Energy Ltd Operations Team

---

<div align="center">

**[View Live Demo](https://mwangitau.github.io/Fuel___Shell_Mangu_Rd_SS/)** • **[Report Issue](#)** • **[Request Feature](#)**

</div>
