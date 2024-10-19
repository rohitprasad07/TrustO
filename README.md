# TrustO
Problem Statement: Incentivizing Environment-Conscious Customers
As consumer awareness about climate change grows, there is a noticeable shift towards adopting environmentally sustainable consumption patterns. The choices individuals make in their everyday lives—ranging from energy use to transportation—directly impact the success of national climate goals. For instance, India's goal to become net-zero by 2070 heavily relies on the collective green choices of its citizens.

However, despite the increasing demand for sustainability, financial institutions currently offer limited rewards or incentives that encourage consumers to make environmentally responsible decisions. Banks, in particular, are in a unique position to influence this shift by integrating climate-conscious behavior into their financial products and services.<!DOCTYPE html>
<html lang="en">

###front-end of the project where user will enter his/her details#######
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Green Score User Data Form</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #e8f5e9;
            margin: 0;
            padding: 0;
        }
        
        .container {
            width: 40%;
            margin: 100px auto;
            background-color: #ffffff;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
            text-align: center;
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 1s ease forwards;
        }
        
        h2 {
            color: #388e3c;
            font-size: 28px;
            margin-bottom: 30px;
            opacity: 0;
            animation: fadeIn 1.5s ease forwards;
            animation-delay: 0.5s;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            font-size: 16px;
            color: #555;
            margin-bottom: 8px;
            text-align: left;
            transition: color 0.3s;
        }
        
        .form-group input {
            width: 100%;
            padding: 12px;
            font-size: 14px;
            border: 1px solid #ccc;
            border-radius: 6px;
            box-sizing: border-box;
            outline: none;
            transition: border 0.3s, box-shadow 0.3s;
        }
        
        .form-group input:focus {
            border-color: #388e3c;
            box-shadow: 0 0 8px rgba(56, 142, 60, 0.4);
        }
        
        .form-group input[type="submit"] {
            background-color: #388e3c;
            color: white;
            font-size: 16px;
            border: none;
            cursor: pointer;
            padding: 15px;
            border-radius: 6px;
            transition: background-color 0.3s, transform 0.2s;
        }
        
        .form-group input[type="submit"]:hover {
            background-color: #2e7d32;
            transform: scale(1.05);
        }
        
        .form-group input[type="text"],
        .form-group input[type="number"],
        .form-group input[type="email"] {
            width: 100%;
        }
        
        .form-group input[type="text"]:hover,
        .form-group input[type="number"]:hover,
        .form-group input[type="email"]:hover {
            border-color: #81c784;
        }
        
        @media (max-width: 768px) {
            .container {
                width: 80%;
            }
        }
        
        @media (max-width: 480px) {
            .container {
                width: 95%;
            }
        }
        /* Keyframes for animations */
        
        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }
        
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        @keyframes shake {
            0% {
                transform: translateX(0);
            }
            25% {
                transform: translateX(-5px);
            }
            50% {
                transform: translateX(5px);
            }
            75% {
                transform: translateX(-5px);
            }
            100% {
                transform: translateX(0);
            }
        }
        
        .shake {
            animation: shake 0.5s;
        }
    </style>
</head>

<body>

    <div class="container">
        <h2>Enter Your Details</h2>
        <form id="userForm">
            <div class="form-group">
                <label for="name">Name:</label>
                <input type="text" id="name" name="name" required>
            </div>
            <div class="form-group">
                <label for="age">Age:</label>
                <input type="number" id="age" name="age" required>
            </div>
            <div class="form-group">
                <label for="mobile">Mobile Number:</label>
                <input type="text" id="mobile" name="mobile" required>
            </div>
            <div class="form-group">
                <label for="email">Email:</label>
                <input type="email" id="email" name="email" required>
            </div>
            <div class="form-group">
                <label for="k_electricity">K Number for Electricity Bill:</label>
                <input type="text" id="k_electricity" name="k_electricity" required>
            </div>
            <div class="form-group">
                <label for="k_water">K Number for Water Bill:</label>
                <input type="text" id="k_water" name="k_water" required>
            </div>
            <div class="form-group">
                <label for="k_lpg">K Number for LPG Bill:</label>
                <input type="text" id="k_lpg" name="k_lpg" required>
            </div>
            <div class="form-group">
                <input type="submit" value="Submit">
            </div>
        </form>
    </div>

    <script>
        // Adding form submission animation and error handling
        document.getElementById('userForm').addEventListener('submit', function(event) {
            event.preventDefault();

            let valid = true;
            const formFields = ['name', 'age', 'mobile', 'email', 'k_electricity', 'k_water', 'k_lpg'];

            // Validation logic (simple validation for non-empty fields)
            formFields.forEach(field => {
                const input = document.getElementById(field);
                if (input.value === '') {
                    input.classList.add('shake');
                    valid = false;
                    setTimeout(() => input.classList.remove('shake'), 500);
                }
            });

            // If all fields are valid, animate form submission
            if (valid) {
                alert("Form submitted successfully!");
                // Further logic to handle submission (API calls or backend connection) can be added here
            }
        });

        // Adding focus animation on form fields
        const inputs = document.querySelectorAll('input');
        inputs.forEach(input => {
            input.addEventListener('focus', () => {
                input.style.boxShadow = '0 0 12px rgba(76, 175, 80, 0.6)';
            });
            input.addEventListener('blur', () => {
                input.style.boxShadow = 'none';
            });
        });
    </script>

</body>

</html>


calulation of carbonfoot print 
import pandas as pd

# Conversion rates
electricity_rate = 7  # ₹ per kWh
water_rate = 20  # ₹ per 1000 liters
lpg_rate = 50  # ₹ per kg of LPG

# Carbon emission factors
electricity_emission_factor = 0.713  # kg CO2 per kWh
water_emission_factor = 0.001  # kg CO2 per liter
lpg_emission_factor = 2.95  # kg CO2 per kg of LPG

def calculate_carbon_footprint(row):
    # Calculate consumption
    electricity_consumption = row['Electricity Bill (₹)'] / electricity_rate  # in kWh
    water_consumption = (row['Water Bill (₹)'] / water_rate) * 1000  # in liters
    lpg_consumption = row['LPG Gas Bill (₹)'] / lpg_rate  # in kg
    
    # Calculate carbon footprint
    electricity_footprint = electricity_consumption * electricity_emission_factor  # in kg CO2
    water_footprint = water_consumption * water_emission_factor  # in kg CO2
    lpg_footprint = lpg_consumption * lpg_emission_factor  # in kg CO2
    
    # Total carbon footprint
    total_footprint = electricity_footprint + water_footprint + lpg_footprint
    return total_footprint

# Load the dataset
df = pd.read_csv('/content/user_bills_with_electricity.csv')

# Calculate carbon footprint for each row
df['Carbon Footprint (kg CO2)'] = df.apply(calculate_carbon_footprint, axis=1)

# Display the result
print(df[['K-number', 'Month', 'Carbon Footprint (kg CO2)']])

# Save the results to a new CSV file
df.to_csv('user_carbon_footprints.csv', index=False)
