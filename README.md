<!DOCTYPE html>
<html>
<head>
    <title>Medicine Reminder</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 20%;
            background-color: #f2f2f2;
        }
        h1 {
            color: #4CAF50;
        }
        #reminder {
            font-size: 20px;
            color: #333;
        }
        button {
            padding: 10px 20px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>
    <h1>Medicine Reminder</h1>
    <p id="reminder">Click the button to set a reminder!</p>
    <button onclick="setReminder()">Set Reminder</button>

    <script>
        function setReminder() {
            const reminderTime = prompt("Enter the time for your reminder (HH:MM, 24-hour format):");
            if (!reminderTime || !/^\d{2}:\d{2}$/.test(reminderTime)) {
                alert("Invalid time format. Please use HH:MM (e.g., 14:30).");
                return;
            }

            const [hours, minutes] = reminderTime.split(':').map(Number);
            const now = new Date();
            const reminder = new Date(now.getFullYear(), now.getMonth(), now.getDate(), hours, minutes, 0);

            if (reminder < now) {
                alert("The time you entered is in the past. Please set a future time.");
                return;
            }

            const delay = reminder - now;
            setTimeout(() => {
                alert("Time to take your medicine!");
                window.open("https://www.yourwebsite.com/medicine-reminder", "_blank"); // Replace with your URL
            }, delay);

            document.getElementById("reminder").textContent = `Reminder set for ${reminderTime}.`;
        }
    </script>
</body>
</html>
