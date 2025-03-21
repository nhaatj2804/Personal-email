# People Data Processing with Apollo API & DeepSeek

This project automates the process of retrieving and processing people data from the Apollo API, generating personalized email content using DeepSeek, and saving the results in a CSV file.

## Features

- Fetches person and organization data from Apollo API.
- Filters and structures relevant data.
- Uses DeepSeek AI to generate personalized email content.
- Saves processed data into a CSV file.
- Logs all actions for easy debugging and monitoring.

## Prerequisites

- Python 3.7+
- An Apollo API Key
- A DeepSeek API Key

## Installation

1. **Clone the repository**

   ```sh
   git clone https://git.nobisoft.com.vn/scm/nst/sales_tool.git
   cd your-repo
   ```

2. **Create a virtual environment (optional but recommended)**

   ```sh
   python -m venv venv
   source venv/bin/activate  # On Windows use: venv\Scripts\activate
   ```

3. **Install dependencies**

   ```sh
   pip install -r requirements.txt
   ```

4. **Set up environment variables**
   - Create a `.env` file in the root directory and add the following:
     ```env
     APOLLO_API_KEY=your_apollo_api_key
     DEEPSEEK_API_KEY=your_deepseek_api_key
     DEEPSEEK_PROMPT="Write a personalized email and a follow-up email for a partnership with Nobisoft. Ensure proper formatting with line breaks so the email are easy to read."
     CSV_FILENAME=result.csv -- This only work for mode 1
     PAGE=1
     PER_PAGE=10
     PERSON_TITLES=ceo,cto
     PERSON_LOCATIONS=usa,uk
     PERSON_SENIORITIES=Executive
     ORGANIZATION_LOCATIONS=usa,uk
     Q_ORGANIZATION_DOMAINS_LIST=apollo.io,microsoft.com
     CONTACT_EMAIL_STATUS=verified,unverified
     ORGANIZATION_IDS=
     ORGANIZATION_NUM_EMPLOYEES_RANGES=1,50
     Q_KEYWORDS=ai, research
     ```

## Usage

### Running the script normally

Run the script using:

```sh
python app.py
```

### Running with input CSV

If you want to provide an input file, use the following command:

```sh
python app.py --input input.csv
```

This will take `input.csv` as input and generate an `input_with_email.csv` with added email content.

**Note:** Both the Deepseek API Key and DeepSeek Prompt are required for both modes.

## How It Works

1. **Search for people**: The script fetches people data from the Apollo API using filters from `.env`.
2. **Process each person**: Extracts relevant details and organization data.
3. **Generate email content**: Uses DeepSeek to generate email subjects and bodies.
4. **Save to CSV**: Stores the processed data in a CSV file.
5. **Log progress**: Tracks execution time and potential errors.

## Logging

- Logs are saved to `app.log`.
- Logs include request statuses, errors, and execution times.

## Troubleshooting

- **Invalid API keys**: Check that your `.env` file contains the correct API keys.
- **Rate limits**: Apollo API has rate limits. If requests fail, try again later.
- **Dependency issues**: Run `pip install -r requirements.txt` to ensure all dependencies are installed.
