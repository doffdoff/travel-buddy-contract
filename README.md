# Travel Buddy - Clarity Smart Contract

## Overview

The **Travel Buddy** smart contract is a decentralized user profile management system for travelers, built using **Clarity** on the **Stacks blockchain**. It allows users to store and manage their travel preferences, history, and personal details in a secure and immutable way.

## Features

- **User Profile Management**: Create, modify, and retrieve traveler profiles based on blockchain identity.
- **Travel Preferences Storage**: Store hobbies, bucket-list destinations, and visited places.
- **Age Verification**: Ensures a valid age range for travelers.
- **Error Handling**: Predefined error messages for better debugging.
- **Efficient Read Operations**: Fetch individual profile details or complete profile summaries.

## Smart Contract Details

### **Data Storage**
The contract maintains a `define-map` called `traveler-data`, which stores the following information:

| Field           | Type                                      | Description                                   |
|----------------|-----------------------------------------|-----------------------------------------------|
| `username`     | `(string-ascii 100)`                    | Traveler's display name                       |
| `years`        | `uint`                                   | Traveler's age                                |
| `hobbies`      | `(list 10 (string-ascii 50))`           | Traveler's interests and hobbies              |
| `bucket-list`  | `(list 5 (string-ascii 100))`           | List of places the traveler wants to visit    |
| `visited-places` | `(list 5 (string-ascii 100))`         | List of places the traveler has already visited |

### **Functions**

#### ✅ **Read-Only Functions**
These functions allow users to retrieve traveler data without modifying the blockchain state.

| Function Name               | Description |
|-----------------------------|-------------|
| `does-profile-exist?`       | Checks if a profile exists for the given user. |
| `fetch-traveler-profile`    | Retrieves the full profile of a traveler. |
| `fetch-traveler-name`       | Fetches only the traveler's username. |
| `fetch-traveler-age`        | Fetches the traveler's age. |
| `fetch-traveler-hobbies`    | Retrieves the traveler's hobbies. |
| `fetch-bucket-list`         | Gets the list of desired travel destinations. |
| `fetch-visited-places`      | Fetches places the traveler has already visited. |
| `count-bucket-list-items`   | Counts the number of destinations on the bucket list. |
| `count-visited-places`      | Counts the number of places visited. |
| `fetch-profile-stats`       | Returns a summary of the user's profile statistics. |

#### 🔄 **Public Functions**
These functions modify the state of the contract and require a blockchain transaction.

| Function Name      | Description |
|-------------------|-------------|
| `create-traveler` | Creates a new traveler profile if none exists. |
| `modify-traveler` | Updates an existing traveler's profile. |

### **Error Handling**
The contract defines several error messages for better debugging:

| Error Code                 | Meaning |
|----------------------------|---------|
| `ERROR-NO-DATA-FOUND (u404)` | Profile not found in the database. |
| `ERROR-RECORD-EXISTS (u409)` | A profile already exists for this user. |
| `ERROR-YEARS-INVALID (u400)` | Invalid age (below 18 or above 120). |
| `ERROR-USERNAME-INVALID (u401)` | Invalid username format. |
| `ERROR-LOCATION-INVALID (u402)` | Invalid location name. |
| `ERROR-HOBBIES-INVALID (u403)` | Invalid hobbies list. |

## How to Use

### **Deploying the Contract**
1. Ensure you have a working **Stacks CLI** and a **Clarity VM** setup.
2. Clone this repository:
   ```sh
   git clone https://github.com/your-username/travel-buddy-contract.git
   cd travel-buddy-contract
