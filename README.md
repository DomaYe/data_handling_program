# Data Handling Program

A comprehensive Python application for generating, storing, and visualizing synthetic data about persons, pets, and occupations. This program demonstrates various data handling capabilities including data generation, multiple export formats, database integration, and data visualization.

## Features

### 🎲 Data Generation
- Generate synthetic data using the Faker library
- Creates three related entities: Persons, Pets, and Occupations
- Configurable number of records
- Realistic relationships between entities (1:N relationships)

### 💾 Multiple Export Formats
- **CSV**: Standard comma-separated values format
- **JSON**: JavaScript Object Notation format
- **XLSX**: Microsoft Excel format with multiple sheets

### 🗄️ Database Integration
- Oracle Database support
- Automatic table creation with proper relationships
- Data insertion with foreign key constraints
- Connection management and error handling

### 📊 Data Visualization
- **Pets per Person**: Bar chart showing pet ownership distribution
- **Pet Species Distribution**: Pie chart of pet species breakdown
- **Pets vs Occupations**: Scatter plot exploring correlations
- **Popular Pet Names**: Bar chart of most common pet names
- All visualizations saved as PNG files

## Requirements

### Python Dependencies
```
pandas
matplotlib
faker
cx_Oracle
openpyxl
```

### System Requirements
- Python 3.7+
- Oracle Instant Client (for database functionality)
- Access to Oracle Database (optional, for database features)

## Installation

1. **Clone or download the project**
   ```bash
   git clone <repository-url>
   cd data_handling_program
   ```

2. **Install Python dependencies**
   ```bash
   pip install pandas matplotlib faker cx_Oracle openpyxl
   ```

3. **Install Oracle Instant Client** (for database functionality)
   - Download from [Oracle's official website](https://www.oracle.com/database/technologies/instant-client.html)
   - Extract to a directory (e.g., `/Users/username/instantclient_21_7`)
   - Update the path in `oracle_handling.py` if different

## Configuration

### Oracle Database Setup
If you want to use the database functionality, update the connection parameters in `oracle_handling.py`:

```python
hostname = "your-oracle-host"
port = 1521
service_name = "your-service-name"
user = "your-username"
password = "your-password"
```

Also update the Oracle Instant Client path:
```python
cx_Oracle.init_oracle_client(lib_dir="path/to/your/instantclient")
```

## Usage

### 1. Generate and Export Data
```bash
python data_handling_program/generator.py
```
This will:
- Generate 10 sample records
- Export to CSV files (`persons.csv`, `pets.csv`, `occupations.csv`)
- Export to JSON files (`persons.json`, `pets.json`, `occupations.json`)
- Export to Excel file (`dataset.xlsx`)

### 2. Store Data in Oracle Database
```bash
python data_handling_program/oracle_handling.py
```
This will:
- Generate 10 sample records
- Create database tables with proper relationships
- Insert data into Oracle database

### 3. Create Visualizations
```bash
python data_handling_program/visualization.py
```
This will:
- Load data from CSV files
- Generate 4 different visualizations
- Save plots as PNG files:
  - `pets_per_person.png`
  - `pet_species_pie.png`
  - `pets_vs_occupations.png`
  - `popular_pet_names.png`

## Project Structure

```
data_handling_program/
├── data_handling_program/
│   ├── __init__.py
│   ├── generator.py          # Data generation and export/import functions
│   ├── oracle_handling.py    # Oracle database operations
│   └── visualization.py      # Data visualization functions
├── README.md
└── output files (generated):
    ├── persons.csv
    ├── pets.csv
    ├── occupations.csv
    ├── persons.json
    ├── pets.json
    ├── occupations.json
    ├── dataset.xlsx
    ├── pets_per_person.png
    ├── pet_species_pie.png
    ├── pets_vs_occupations.png
    └── popular_pet_names.png
```

## Data Model

### Person
- `person_id`: Unique identifier
- `full_name`: Full name of the person
- `address`: Address of the person

### Pet
- `pet_id`: Unique identifier (format: "{owner_id}_{pet_index}")
- `owner_id`: Foreign key to Person
- `pet_name`: Name of the pet
- `species`: Type of pet (Dog, Cat, Bird, Rabbit)

### Occupation
- `occupation_id`: Unique identifier (format: "{person_id}_{occupation_index}")
- `person_id`: Foreign key to Person
- `occupation`: Job title
- `company`: Company name

## Customization

### Changing Number of Records
Modify the `num_records` parameter in the main sections of each file:
```python
persons, pets, occupations = generate_data(50)  # Generate 50 records instead of 10
```

### Adding New Pet Species
Update the species list in `generator.py`:
```python
species=random.choice(['Dog', 'Cat', 'Bird', 'Rabbit', 'Fish', 'Hamster'])
```

### Customizing Visualizations
Modify the plotting functions in `visualization.py` to change colors, sizes, or add new chart types.

## Error Handling

The application includes comprehensive error handling for:
- File not found errors
- Database connection issues
- Empty data files
- Visualization rendering problems

## Dependencies

- **pandas**: Data manipulation and analysis
- **matplotlib**: Data visualization
- **faker**: Synthetic data generation
- **cx_Oracle**: Oracle database connectivity
- **openpyxl**: Excel file handling

## License

[Add your license information here]

## Contributing

[Add contribution guidelines if applicable]

## Support

[Add contact information or support details if applicable] 