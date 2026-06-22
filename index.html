<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SMC Access Control System</title>
    <script src="https://unpkg.com/html5-qrcode"></script>
    <style>
        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            background-color: #121824;
            color: #ffffff;
            margin: 0;
            padding: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .container {
            width: 100%;
            max-width: 450px;
            background: #1a2333;
            padding: 20px;
            border-radius: 16px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            box-sizing: border-box;
        }
        h2 {
            text-align: center;
            margin-top: 0;
            color: #f4f6f9;
            font-size: 1.5rem;
        }
        #reader {
            width: 100%;
            border-radius: 12px;
            overflow: hidden;
            border: none !important;
            background: #243146;
        }
        /* Ticket Display Layout (Matching the screenshot style) */
        .ticket-card {
            margin-top: 25px;
            background: #171d29;
            border-radius: 12px;
            overflow: hidden;
            border-top: 6px solid #ff6b00; /* Distinct top accent line */
            display: none;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }
        .status-header {
            padding: 12px;
            font-weight: bold;
            font-size: 1.1rem;
            text-align: center;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        .status-granted { background-color: #10b981; color: white; }
        .status-denied { background-color: #ef4444; color: white; }
        .status-duplicate { background-color: #f59e0b; color: white; }

        .ticket-body {
            padding: 25px 20px;
            text-align: left;
        }
        .brand-logo {
            font-weight: 800;
            font-size: 1.3rem;
            color: #ffffff;
            margin-bottom: 25px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .brand-icon {
            width: 24px;
            height: 24px;
            background: linear-gradient(135deg, #0076ff, #ff6b00);
            border-radius: 6px;
            transform: rotate(45deg);
        }
        .field-group {
            margin-bottom: 18px;
        }
        .field-label {
            font-size: 0.75rem;
            text-transform: uppercase;
            color: #718096;
            letter-spacing: 1.5px;
            margin-bottom: 4px;
            font-weight: 600;
        }
        .field-value {
            font-size: 1.05rem;
            color: #edf2f7;
            font-weight: 500;
        }
        .divider {
            height: 1px;
            background: #2d3748;
            margin-bottom: 20px;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>SMC Dinner Check-In</h2>
    <div id="reader"></div>

    <div id="ticketCard" class="ticket-card">
        <div id="statusBanner" class="status-header">Access Granted</div>
        
        <div class="ticket-body">
            <div class="brand-logo">
                <div class="brand-icon"></div>
                SMC 26
            </div>
            
            <div class="divider"></div>

            <div class="field-group">
                <div class="field-label">Full Name</div>
                <div id="displayName" class="field-value">Pastor Ankomah Prince</div>
            </div>

            <div class="field-group">
                <div class="field-label">Church / Ministry</div>
                <div id="displayChurch" class="field-value">Grace Temple</div>
            </div>

            <div class="field-group">
                <div class="field-label">Position / Function / Role</div>
                <div id="displayRole" class="field-value">Youth Leader</div>
            </div>
        </div>
    </div>
</div>

<script>
    // MOCK DATABASE 
    // In production, this data is pulled from your Google Sheet master file
    const guestDatabase = {
        "SMC-001": { 
            title: "Mr.", 
            name: "Ankomah Prince", 
            church: "Grace Temple Assembly", 
            role: "Youth Organizer", 
            dinnerAccess: true, 
            checkedIn: false 
        },
        "SMC-002": { 
            title: "Pastor", 
            name: "Sussan Dissan", 
            church: "Faith Ministries", 
            role: "Head Pastor", 
            dinnerAccess: false, 
            checkedIn: false 
        },
        "SMC-003": { 
            title: "Evang.", 
            name: "John Doe", 
            church: "Global Revival Church", 
            role: "Evangelist", 
            dinnerAccess: true, 
            checkedIn: true // Simulate someone who already entered
        }
    };

    function processAccess(guestId) {
        const card = document.getElementById('ticketCard');
        const banner = document.getElementById('statusBanner');
        const nameField = document.getElementById('displayName');
        const churchField = document.getElementById('displayChurch');
        const roleField = document.getElementById('displayRole');

        card.style.display = "block";

        // 1. Check if guest is registered
        if (!guestDatabase[guestId]) {
            banner.className = "status-header status-denied";
            banner.innerText = "❌ Invalid Ticket";
            nameField.innerText = "Unknown Code Generated";
            churchField.innerText = "N/A";
            roleField.innerText = "N/A";
            return;
        }

        const guest = guestDatabase[guestId];

        // Fill data dynamically combines Title + Name
        nameField.innerText = `${guest.title} ${guest.name}`;
        churchField.innerText = guest.church;
        roleField.innerText = guest.role;

        // 2. Evaluate Dinner Access Permissions
        if (!guest.dinnerAccess) {
            banner.className = "status-header status-denied";
            banner.innerText = "❌ Access Denied (No Dinner Pass)";
            return;
        }

        // 3. Evaluate Double Entry Check
        if (guest.checkedIn) {
            banner.className = "status-header status-duplicate";
            banner.innerText = "⚠️ Duplicate Ticket (Already Inside)";
            return;
        }

        // 4. Successful Access Granted
        guest.checkedIn = true; // Mark used locally
        banner.className = "status-header status-granted";
        banner.innerText = "✅ Access Granted";
    }

    // Initialize Camera Scan Rules
    function onScanSuccess(decodedText, decodedResult) {
        html5QrcodeScanner.clear(); // Pause camera feed
        processAccess(decodedText);

        // Resume scanning loop after 4 seconds for the next attendee
        setTimeout(() => {
            html5QrcodeScanner.render(onScanSuccess);
        }, 4000);
    }

    const html5QrcodeScanner = new Html5QrcodeScanner("reader", { fps: 10, qrbox: 250 });
    html5QrcodeScanner.render(onScanSuccess);
</script>

</body>
  </html>
