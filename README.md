# SWIL ERP Report Automation

![Python](https://img.shields.io/badge/python-3.8+-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Status](https://img.shields.io/badge/status-active-success.svg)

Automated report generation and data extraction tool for SWIL ERP system. This Python-based solution streamlines the process of generating various business reports including sales, purchases, inventory, and GST reports directly from your SWIL ERP database.

## 🚀 Features

- **Automated Report Generation**: Generate sales, purchase, inventory, and GST reports automatically
- **Multiple Report Types**:
  - Sales Reports (daily, weekly, monthly)
  - Purchase Reports with supplier details
  - Inventory Status Reports
  - GST Reports (GSTR1, GSTR3B compatible)
- **Excel Export**: Professional Excel reports with multiple sheets and summaries
- **Scheduled Reports**: Set up automated report generation with cron-like scheduling
- **Branch Filtering**: Generate reports for specific branches or all branches
- **Configurable**: Easy configuration through JSON file
- **Logging**: Comprehensive logging for tracking and debugging

## 💻 Prerequisites

- Python 3.8 or higher
- Access to SWIL ERP database
- Basic understanding of Python

## 📦 Installation

1. **Clone the repository**
```bash
git clone https://github.com/AmythP/swil-erp-report-automation.git
cd swil-erp-report-automation
```

2. **Create virtual environment** (recommended)
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Configure the application**

Edit `config.json` with your SWIL ERP database credentials:
```json
{
  "swil_erp": {
    "database_host": "your_host",
    "database_port": 3306,
    "database_name": "your_db_name",
    "database_user": "your_username",
    "database_password": "your_password"
  }
}
```

## 🛠️ Usage

### Basic Usage

Run the script to generate reports for the current month:

```bash
python swil_report_generator.py
```

### Generate Specific Reports

```python
from swil_report_generator import SWILERPReportGenerator

# Initialize
generator = SWILERPReportGenerator()

# Generate sales report
sales_report = generator.generate_sales_report(
    start_date='2025-01-01',
    end_date='2025-01-31',
    branch='Main Branch'  # Optional
)

# Generate purchase report
purchase_report = generator.generate_purchase_report(
    start_date='2025-01-01',
    end_date='2025-01-31'
)

# Generate inventory report
inventory_report = generator.generate_inventory_report()

# Generate GST report
gst_report = generator.generate_gst_report(
    start_date='2025-01-01',
    end_date='2025-01-31',
    report_type='GSTR1'
)
```

### Scheduled Reports

Set up automated report generation in `config.json`:

```json
{
  "report_schedule": {
    "sales_daily": "0 9 * * *",
    "inventory_weekly": "0 9 * * 1",
    "gst_monthly": "0 9 1 * *"
  }
}
```

## 📁 Project Structure

```
swil-erp-report-automation/
├── swil_report_generator.py  # Main application code
├── requirements.txt          # Python dependencies
├── config.json               # Configuration file
├── README.md                 # This file
├── .gitignore                # Git ignore patterns
├── reports/                  # Generated reports (auto-created)
└── data/                     # Data directory (auto-created)
```

## ⚙️ Configuration

The `config.json` file contains all configuration options:

```json
{
  "output_directory": "reports",
  "data_directory": "data",
  "report_formats": ["excel", "csv"],
  "date_format": "%Y-%m-%d",
  "currency_symbol": "₹",
  "swil_erp": {
    "database_host": "localhost",
    "database_port": 3306,
    "database_name": "swil_erp"
  }
}
```

## 📊 Report Types

### Sales Report
- Detailed transaction listing
- Summary with totals
- Branch-wise breakdown (optional)
- GST calculations

### Purchase Report
- Purchase order details
- Supplier information
- Amount breakdowns
- Status tracking

### Inventory Report
- Current stock levels
- Reorder levels
- Product categorization
- Low stock alerts

### GST Report
- GSTR1 format
- Tax calculations (CGST, SGST, IGST)
- Invoice-wise details
- Ready for filing

## 🔧 Customization

You can extend the functionality by:

1. **Adding new report types**: Create new methods in the `SWILERPReportGenerator` class
2. **Custom data sources**: Modify the `_fetch_*_data` methods to connect to your specific database
3. **Different formats**: Add CSV, PDF, or other export formats
4. **Email integration**: Add email functionality to send reports automatically

## 💡 Use Cases

- **Daily Sales Tracking**: Automatically generate and email daily sales reports
- **Monthly GST Filing**: Generate GST-ready reports for tax filing
- **Inventory Management**: Monitor stock levels and get low-stock alerts
- **Purchase Analytics**: Track supplier performance and purchase trends
- **Multi-branch Management**: Consolidate or separate reports by branch

## 👥 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📝 License

This project is licensed under the MIT License.

## 👤 Author

**Amrut Prakash**
- GitHub: [@AmythP](https://github.com/AmythP)
- Location: Indore, India

## 📞 Support

For issues, questions, or suggestions, please open an issue on GitHub.

## 📝 Changelog

### Version 1.0.0 (2025-11-11)
- Initial release
- Sales, Purchase, Inventory, and GST report generation
- Excel export functionality
- Configurable settings
- Logging support

---

**Note**: This tool is designed to work with SWIL ERP systems. Make sure you have proper database access credentials before using this tool.