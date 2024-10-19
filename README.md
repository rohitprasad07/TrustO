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
    electricity_df = pd.DataFrame(electricity_data)
    water_df = pd.DataFrame(water_data)
    lpg_df = pd.DataFrame(lpg_data)

    # Saving individual DataFrames to CSV files
    electricity_df.to_csv(f'/content/electricity_bill_{electricity_user}.csv', index=False)
    water_df.to_csv(f'/content/water_bill_{water_user}.csv', index=False)
    lpg_df.to_csv(f'/content/lpg_bill_{lpg_user}.csv', index=False)

    print("Individual bill files created for respective users.")

# Function to create combined CSV file
def create_combined_file(electricity_user, water_user, lpg_user):
    # Load individual bill DataFrames
    electricity_df = pd.read_csv(f'/content/electricity_bill_{electricity_user}.csv')
    water_df = pd.read_csv(f'/content/water_bill_{water_user}.csv')
    lpg_df = pd.read_csv(f'/content/lpg_bill_{lpg_user}.csv')

    # Merging DataFrames based on Month
    combined_df = pd.merge(electricity_df, water_df, on=["Month"], suffixes=('_Electricity', '_Water'))
    combined_df = pd.merge(combined_df, lpg_df, on=["Month"])

    # Saving the combined DataFrame to a CSV file
    combined_df.to_csv(f'/content/combined_bills_{lpg_user}.csv', index=False)

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






