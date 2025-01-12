# Loop-ai-assignment
# Business Hour Mismatch Analysis for Grubhub and UberEats

This project aims to analyze business hour mismatches between two popular food delivery platforms, Grubhub and UberEats. The focus is to identify discrepancies in store operating hours across both platforms and generate a report that classifies the mismatch status as "In Range," "Out of Range," or "Out of Range with 5 mins difference."

## Objective

The goal is to compute a metric called **business hour mismatch** for each restaurant between Grubhub and UberEats. For simplicity, we assume UberEats as the **ground truth** and check if the Grubhub business hours are consistent with UberEats hours.

## Data Sources

1. **UberEats**: The dataset contains the store business hours in JSON format. This data can be queried from BigQuery.
2. **Grubhub**: The dataset contains business hours in a structured JSON response format.

## Key Steps

1. **Data Extraction**: 
   - Extract business hours for each store from both Grubhub and UberEats datasets.
   
2. **Data Transformation**:
   - Flatten and parse the JSON data for both platforms to extract business hours, including opening and closing times.
   
3. **Data Comparison**:
   - Compare the business hours between Grubhub and UberEats.
   - Categorize the mismatch into the following categories:
     - **In Range**: Grubhub hours match UberEats hours.
     - **Out of Range**: Grubhub hours do not match UberEats hours.
     - **Out of Range with 5 mins difference**: Grubhub hours are within 5 minutes of UberEats hours.

4. **Output**:
   - Generate a table displaying:
     - Grubhub and UberEats business hours
     - The mismatch status ("In Range", "Out of Range", "Out of Range with 5 mins difference")

## Technologies Used

- **BigQuery**: Used for querying the datasets and performing transformations.
- **SQL**: Used to write queries for extracting, transforming, and comparing business hours.
- **JSON**: Data is stored in JSON format and parsed using BigQuery's JSON functions.

## Instructions

### Step 1: Create a BigQuery Sandbox
- Set up a BigQuery environment and verify access to UberEats and Grubhub datasets.

### Step 2: Extract Data from Grubhub
- Parse and extract business hours from the Grubhub dataset using SQL.

### Step 3: Extract Data from UberEats
- Similarly, extract business hours from the UberEats dataset using SQL.

### Step 4: Join Grubhub and UberEats Tables
- Join both datasets based on a common store identifier (slug).

### Step 5: Compare Business Hours
- Compare the business hours between Grubhub and UberEats and categorize the mismatch.

### Step 6: Generate Output
- Output the final table showing the mismatch status for each store.

## Example Output

| Grubhub Slug | UberEats Slug | Grubhub Business Hours | UberEats Business Hours | Mismatch Status                |
|--------------|---------------|------------------------|-------------------------|--------------------------------|
| johnspizz    | johnspizz     | 10:00 - 22:00          | 10:00 - 22:00           | In Range                      |
| pizzahut     | pizzahut      | 11:00 - 23:00          | 11:00 - 22:30           | Out of Range                  |
| tacoqueen    | tacoqueen     | 09:00 - 20:00          | 09:05 - 20:00           | Out of Range with 5 mins diff |

## How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/business-hour-mismatch-analysis.git
