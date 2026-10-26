# User Data Pipeline

## Description
A simple mini data pipeline built for practicing ETL (Extract, Transform, Load).
This script pulls user data from a public API, extracts the required fields,
and saves the result as a clean, ready-to-use CSV file.

## Data Source
Data is fetched from [JSONPlaceholder](https://jsonplaceholder.typicode.com/users),
a fake REST API that provides dummy data (users, posts, comments, etc.) for
testing and practice purposes.

## Pipeline
The process flow executed by the script:

```text
API (JSONPlaceholder)
        ↓
Extract    → fetch user data with requests
        ↓
Transform  → JSON → DataFrame, extract city from nested address
        ↓
Clean      → keep only name, email, city
        ↓
Load       → save to clean_user.csv
```

1. **Extract** — Fetch user data from the `/users` endpoint using `requests`.
2. **Transform** — Convert the JSON response into a DataFrame, then extract
   the `city` field from the nested `address` object.
3. **Clean** — Filter the columns, keeping only `name`, `email`, and `city`.
4. **Load** — Save the final result to a `clean_user.csv` file.

Since the transformation happens before the data is saved to its destination,
this pipeline follows the **ETL** pattern.

## Project Structure
```text
.
├── main.py            # pipeline script
├── clean_user.csv     # sample output
├── requirements.txt   # dependencies
├── .gitignore
└── README.md
```

## Requirements
- Python 3.x
- Libraries:
  - `requests`
  - `pandas`

Install dependencies:
```bash
pip install -r requirements.txt
```

## How to Run
1. Make sure the dependencies are installed.
2. Run the script:
```bash
python main.py
```
3. Once finished, the output will be available in the `clean_user.csv` file in the same folder.

## Sample Output
`clean_user.csv`:

| name | email | city |
|------|-------|------|
| Leanne Graham | Sincere@april.biz | Gwenborough |
| Ervin Howell | Shanna@melissa.tv | Wisokyburgh |
| Clementine Bauch | Nathan@yesenia.net | McKenziehaven |
| Patricia Lebsack | Julianne.OConner@kory.org | South Elvis |
| Chelsey Dietrich | Lucio_Hettinger@annie.ca | Roscoeview |

The API returns 10 users, so the CSV contains 10 rows (plus the header).

## Author
Kevin ([@kevinnaratech](https://github.com/kevinnaratech))
