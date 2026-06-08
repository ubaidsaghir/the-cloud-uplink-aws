# ☁️ The Cloud Uplink — AWS

<div align="center">

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![AWS S3](https://img.shields.io/badge/AWS_S3-Storage-FF9900?style=for-the-badge&logo=amazons3&logoColor=white)
![Boto3](https://img.shields.io/badge/Boto3-SDK-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-DataFrame-150458?style=for-the-badge&logo=pandas&logoColor=white)
![WeatherAPI](https://img.shields.io/badge/WeatherAPI-Live_Data-00BCD4?style=for-the-badge&logo=cloudflare&logoColor=white)

**A Python pipeline that fetches live weather data for Pakistani cities and uploads it directly to AWS S3.**

</div>

---

## What This Project Does

**The Cloud Uplink** is an end-to-end data pipeline that:

1. Fetches **live weather data** (temperature, humidity) for multiple cities using WeatherAPI
2. Transforms the raw API response into a clean **CSV file** using Pandas
3. ☁️ Uploads the CSV file directly to an **AWS S3 bucket** using Boto3

This project simulates a real-world **cloud data ingestion task** — a foundational pattern in data engineering pipelines.

---

## Cities Covered

| City | Country |
|------|---------|
| Multan | 🇵🇰 Pakistan |
| Lahore | 🇵🇰 Pakistan |
| Islamabad | 🇵🇰 Pakistan |

---

## Project Structure

```
the-cloud-uplink-aws/
│
├── The Cloud Uplink(AWS)/
│   └── uplink.py          # Main pipeline script
│
└── README.md
```

---

## ⚙️ How It Works

```
WeatherAPI (Live Data)
        ↓
   requests.get()          ← Fetches weather JSON for each city
        ↓
   Pandas DataFrame         ← Structures: city, temp_c, humidity, timestamp
        ↓
   df.to_csv()              ← Saves as City_Data.csv locally
        ↓
   boto3 S3 Upload          ← Pushes the CSV to AWS S3 bucket
```

---

## Dependencies

Install all required libraries:

```bash
pip install boto3 requests pandas
```

| Library | Purpose |
|---------|---------|
| `requests` | Makes HTTP calls to WeatherAPI |
| `pandas` | Builds and exports the DataFrame as CSV |
| `boto3` | AWS SDK — handles S3 authentication & upload |

---

## Setup & Configuration

### 1. WeatherAPI Key
Get a free API key from [weatherapi.com](https://www.weatherapi.com) and replace it in the script:

```python
"key": "YOUR_WEATHERAPI_KEY"
```

### 2. AWS Credentials
Configure your AWS credentials using the AWS CLI:

```bash
aws configure
```

You'll be prompted to enter:
- **AWS Access Key ID**
- **AWS Secret Access Key**
- **Default Region** (e.g., `us-east-1`)

> ⚠️ **Never hardcode your AWS credentials in the script.** Always use `aws configure` or environment variables.

### 3. S3 Bucket
Make sure your S3 bucket already exists. Update the bucket name in the script if needed:

```python
bucket_name = "your-s3-bucket-name"
```

---

## ▶️ Running the Script

```bash
python uplink.py
```

**Expected Output:**

```
csv created
File uploaded to S3
```

After running, your `City_Data.csv` will appear in your S3 bucket with this structure:

```
city,temp,humidity,timestamp
Multan,38.0,25,2025-06-08 14:32:00
Lahore,34.5,40,2025-06-08 14:32:01
Islamabad,30.1,55,2025-06-08 14:32:02
```

---

## Security Note

- Do **not** commit your WeatherAPI key or AWS credentials to GitHub
- Add a `.gitignore` to exclude any `.env` files or credential configs:

```
.env
*.csv
__pycache__/
```

---

## Concepts Practiced

- REST API consumption with Python (`requests`)
- Data structuring with `pandas`
- Cloud storage integration via **AWS S3 + Boto3**
- Real-world data pipeline pattern: **Extract → Transform → Load (ETL)**

---

## Author

**Ubaid Saghir**  
Cloud & Data Engineering Training · Week 5  
🔗 [github.com/ubaidsaghir](https://github.com/ubaidsaghir)

---

<div align="center">
  <sub>Built with ☁️ as part of a structured cloud data engineering program</sub>
</div>
