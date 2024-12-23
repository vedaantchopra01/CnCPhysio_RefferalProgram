<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CnC Physiotherapy Referral Program</title>
    <style>
        /* General Styling */
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #000;
            color: #fff;
        }

        /* Header Styling */
        header {
            text-align: center;
            padding: 20px;
            background-color: #111;
            border-bottom: 2px solid #444;
        }

        header h1 {
            font-size: 2.8em;
            font-weight: bold;
            margin: 10px 0;
        }

        header p {
            font-size: 1.2em;
            margin: 5px 0;
        }

        /* Main Container Styling */
        .container {
            max-width: 650px;
            margin: 30px auto;
            background: #222;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(255, 255, 255, 0.1);
        }

        .container h2 {
            text-align: center;
            margin-bottom: 15px;
            font-size: 1.8em;
            color: #ffd700;
        }

        .note {
            font-size: 1.1em;
            line-height: 1.6;
            text-align: justify;
            margin-bottom: 20px;
        }

        form {
            margin-top: 20px;
        }

        /* Form Input Styling */
        label {
            display: block;
            text-align: left;
            font-size: 1.1em;
            margin-top: 15px;
        }

        input, select, button {
            width: 100%;
            padding: 12px;
            margin-top: 8px;
            border: 1px solid #555;
            border-radius: 5px;
            background: #333;
            color: #fff;
            font-size: 1em;
        }

        button {
            background-color: #444;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        button:hover {
            background-color: #555;
        }

        /* Referral Code Display */
        .referral-code {
            margin-top: 20px;
            font-size: 1.3em;
            font-weight: bold;
            text-align: center;
            padding: 10px;
            background: #111;
            border: 1px solid #444;
            border-radius: 8px;
        }

        /* WhatsApp Button Styling */
        .whatsapp-button {
            background-color: #25d366;
            color: #fff;
            padding: 12px;
            border: none;
            border-radius: 5px;
            font-size: 1em;
            cursor: pointer;
            width: 100%;
            margin-top: 20px;
            text-align: center;
        }

        .whatsapp-button:hover {
            background-color: #1db954;
        }
    </style>
</head>
<body>
    <header>
        <h1>CnC Physiotherapy Clinic</h1>
        <p>"We Treat but He Cures"</p>
        <p>Sector 122: D-127, Sector 122, Noida</p>
        <p>Sector 17: BHEL Dispensary, Sector 17, Noida</p>
    </header>

    <div class="container">
        <h2>Referral Program</h2>
        <p class="note">
            Refer your friends and get <strong>2 Dry Cupping Sessions</strong> or 
            <strong>1 Physiotherapy Session</strong> for free!<br>
            Your friend will also get <strong>₹1000 off</strong> on our services.<br>
            Just fill out the form below and share the referral code via WhatsApp!
        </p>

        <form id="referralForm">
            <label for="name">Your Name:</label>
            <input type="text" id="name" name="name" placeholder="Enter your name" required>

            <label for="phone">Phone Number:</label>
            <input type="tel" id="phone" name="phone" placeholder="Enter your phone number" required>

            <label for="branch">Which CnC Physiotherapy branch did you visit?</label>
            <select id="branch" name="branch" required>
                <option value="" disabled selected>Select your branch</option>
                <option value="Sector 122">D-127, Sector 122, Noida</option>
                <option value="Sector 17">BHEL Dispensary, Sector 17, Noida</option>
            </select>

            <button type="submit">Generate Referral Code</button>
        </form>

        <div class="referral-code" id="referralCode"></div>
        <div id="whatsappShare" style="text-align: center; margin-top: 20px;"></div>
    </div>

    <script>
        document.getElementById("referralForm").addEventListener("submit", function(event) {
            event.preventDefault();

            // Get form values
            const name = document.getElementById("name").value.trim();
            const branch = document.getElementById("branch").value;

            // Generate referral code
            const referralCode = `CnC_122_Referral_${name.replace(/\s+/g, '_')}`;

            // Display referral code
            const referralCodeDiv = document.getElementById("referralCode");
            referralCodeDiv.innerHTML = `
                <p>Your Referral Code:</p>
                <p>${referralCode}</p>
                <p>Share this code with your family and friends!</p>
            `;

            // Generate WhatsApp share link
            const whatsappMessage = encodeURIComponent(
                `Hi! I visited CnC Physiotherapy Clinic (${branch}) and got amazing treatment. Use my referral code "${referralCode}" to get ₹1000 off on services!`
            );

            const whatsappLink = `https://wa.me/?text=${whatsappMessage}`;
            const whatsappShareDiv = document.getElementById("whatsappShare");
            whatsappShareDiv.innerHTML = `
                <button class="whatsapp-button" onclick="window.open('${whatsappLink}', '_blank')">
                    Share on WhatsApp
                </button>
            `;
        });
    </script>
</body>
</html>
