# Typescript

# Explanation of the Code
The code provided calculates the monthly usage statistics for users based on their session data. Here's a step-by-step explanation of how the code works:

Types
Session

# Represents a user session with the following properties:
deviceId: Identifier for the device.
userId: Identifier for the user.
logged_in: Timestamp when the user logged in.
logged_out: Timestamp when the user logged out.
lastOpenedAt: Timestamp of the last activity during the session.
MonthlyUsage

# Represents the monthly usage statistics:
month: A string in the format "YYYY-MM" representing the month.
loggedInUsers: A set of unique user IDs who were logged in during the month.
activeUsers: A set of unique user IDs who were active during the month.
Function: getMonthlyUsage
This function processes an array of Session objects and returns an array of MonthlyUsage objects.

# Initialize monthlyUsageMap:

An object to store usage statistics keyed by month.
Loop through each session:

Extract userId, logged_in, logged_out, and lastOpenedAt from the session.
Determine the months spanned by this session using the logged_in and logged_out timestamps.
Create date objects for the start and end months.
Iterate over each month in the session range:

Convert the currentMonth to a string key in the format "YYYY-MM".
Check if this month key exists in monthlyUsageMap. If not, initialize a new MonthlyUsage object for this month.
Add the userId to the loggedInUsers set for this month.
Check if lastOpenedAt falls within the currentMonth:
If so, add the userId to the activeUsers set for this month.
Move to the next month by incrementing the currentMonth.
Return the monthly usage statistics:

Convert the monthlyUsageMap values to an array and return it.
Example Usage
The example creates two Session objects and calls the getMonthlyUsage function with these sessions. The result is logged to the console.

# Explanation of Example
# Session 1:

user1 logs in on January 10, 2023, and logs out on June 15, 2023.
user1 is active in April 2023.
Session 2:

user2 logs in on February 5, 2023, and logs out on March 25, 2023.
user2 is active in March 2023.

# Result:

The usage variable will contain monthly usage statistics from January 2023 to June 2023, indicating which users were logged in and active each month.

Explanation of Monthly Usage Calculation
For each month within the session range, we:

Add the user to the loggedInUsers set.
Add the user to the activeUsers set if the lastOpenedAt date falls within that month.
