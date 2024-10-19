# TrustO
Problem Statement: Incentivizing Environment-Conscious Customers
As consumer awareness about climate change grows, there is a noticeable shift towards adopting environmentally sustainable consumption patterns. The choices individuals make in their everyday lives—ranging from energy use to transportation—directly impact the success of national climate goals. For instance, India's goal to become net-zero by 2070 heavily relies on the collective green choices of its citizens.

However, despite the increasing demand for sustainability, financial institutions currently offer limited rewards or incentives that encourage consumers to make environmentally responsible decisions. Banks, in particular, are in a unique position to influence this shift by integrating climate-conscious behavior into their financial products and services.<!DOCTYPE html>
<html lang="en">



import pandas as pd

# Data for Electricity Bill (12 months)
electricity_data = {
    "Username": ["user_e1"] * 12,
    "Month": ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"],
    "Electricity Bill (₹)": [3500, 3400, 3700, 3600, 3900, 4100, 3800, 4000, 3950, 4300, 4500, 4200]
}

# Data for Water Bill (12 months)
water_data = {
    "Username": ["user_w1"] * 12,
    "Month": ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"],
    "Water Bill (₹)": [800, 780, 790, 770, 810, 820, 750, 740, 760, 730, 800, 820]
}

# Data for LPG Bill (12 months)
lpg_data = {
    "Username": ["user_l1"] * 12,
    "Month": ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"],
    "LPG Bill (₹)": [900, 920, 910, 930, 940, 950, 970, 990, 980, 960, 1000, 1050]
}

# Creating DataFrames
electricity_df = pd.DataFrame(electricity_data)
water_df = pd.DataFrame(water_data)
lpg_df = pd.DataFrame(lpg_data)

# Saving DataFrames to CSV files
electricity_df.to_csv('/content/electricity_bills.csv', index=False)
water_df.to_csv('/content/water_bills.csv', index=False)
lpg_df.to_csv('/content/lpg_bills.csv', index=False)

# Function to display bills for a given username
def display_bills(electricity_username, water_username, lpg_username):
    # Filter DataFrames based on the usernames
    electricity_bills = electricity_df[electricity_df["Username"] == electricity_username]
    water_bills = water_df[water_df["Username"] == water_username]
    lpg_bills = lpg_df[lpg_df["Username"] == lpg_username]

    # Check if any bills exist for the electricity username and print them
    if not electricity_bills.empty:
        print("\nElectricity Bills for", electricity_username)
        print(electricity_bills)
    else:
        print(f"\nNo electricity bills found for {electricity_username}.")

    # Check if any bills exist for the water username and print them
    if not water_bills.empty:
        print("\nWater Bills for", water_username)
        print(water_bills)
    else:
        print(f"\nNo water bills found for {water_username}.")

    # Check if any bills exist for the LPG username and print them
    if not lpg_bills.empty:
        print("\nLPG Bills for", lpg_username)
        print(lpg_bills)
    else:
        print(f"\nNo LPG bills found for {lpg_username}.")

# Prompting user for usernames
electricity_username_input = input("Enter the username for Electricity Bills: ")
water_username_input = input("Enter the username for Water Bills: ")
lpg_username_input = input("Enter the username for LPG Bills: ")

# Displaying bills for the entered usernames
display_bills(electricity_username_input, water_username_input, lpg_username_input)





