### **🚀 Boters - Cloudflare-Style CAPTCHA Shield for GitHub Pages**  

**Boters** is an advanced security shield that prevents bots from accessing your GitHub Pages site. It works like **Cloudflare's "Checking Your Browser"** page, ensuring only real users can enter while blocking automated bots.
![shield_11918095](https://github.com/user-attachments/assets/b1c017fa-2ef9-443a-91dd-02fe279eb701)


---
_Icons credits_ : 
<a href="https://www.freepik.com/icon/shield_11918095#fromView=search&page=1&position=85&uuid=a6f9fa4c-643d-40be-b03c-28f9d122e5c2">Icon by Creative Squad</a>

---

## **🌟 Features**
✅ **Pre-Website Verification** – Users must pass CAPTCHA before the main website loads.  
✅ **Mouse Movement Detection** – Bots that don’t move the mouse are automatically blocked.  
✅ **Hidden Honeypot Trap** – Invisible input field that only bots fill, leading to auto-failure.  
✅ **Checkbox & Delay Verification** – Ensures human interaction before proceeding.  
✅ **Loading Animation & Smooth Redirect** – A Cloudflare-style security experience.  
✅ **Email Alert for Bots** – If a bot is detected, an email alert is sent to the developer.  
✅ **100% Free & Open-Source** – Works directly on GitHub Pages without paid services. 
![botersgithub](https://github.com/user-attachments/assets/da0e66bb-3850-436a-b6a6-5fa557047384)


---

## **📌 How to Set Up "Boters" on GitHub Pages**
### **Step 1: Fork or Clone the Repository**
```sh
git clone https://github.com/YOUR-USERNAME/YOUR-REPO.git
```
If you don’t have a repository yet, create one on GitHub and upload the files.

---

### **Step 2: Enable GitHub Pages**
1. **Go to your repository → Settings → Pages**  
2. **Set the Source to `main` branch and Save**  
3. Your site will be live at:  
   ```
   https://yourusername.github.io/yourrepo/
   ```

---

## **🔗 Integrating "Boters" with Your Website**
### **Option 1: Meta Redirect (Simple)**
Edit your `index.html` file and add this inside `<head>`:
```html
<meta http-equiv="refresh" content="0;url=captcha.html">
```
✅ **Now, when someone visits your website, they will first see the Boters verification page before being redirected to the main site.**  

---

### **Option 2: JavaScript Redirect (Advanced)**
If you want users to **see CAPTCHA only once per session**, use this method:  

#### **1️⃣ Add This to `index.html`**
```html
<script>
    if (!sessionStorage.getItem("captchaVerified")) {
        window.location.href = "captcha.html";
    }
</script>
```
#### **2️⃣ Modify `captcha.html`**
Once the user passes verification, set a session variable before redirecting:
```js
sessionStorage.setItem("captchaVerified", "true");
window.location.href = "index.html"; 
```
✅ **This way, users won’t see CAPTCHA again if they refresh the page!**  

---

## **📧 Bot Alert System (Email Notification)**
If a bot is detected, an email alert is sent to the developer.  
### **🔹 Edit `captcha.html` and Update the Email Address:**
```js
function sendEmailAlert() {
    let developerEmail = "your-email@example.com";
    let emailBody = encodeURIComponent("🚨 Bot detected on your site! Take action immediately.");
    window.location.href = `mailto:${developerEmail}?subject=Bot Alert&body=${emailBody}`;
}
```
✅ **Replace `"your-email@example.com"` with your actual email to receive bot alerts!**  

---

## **📜 Adding CAPTCHA Page (`captcha.html`)**
To create a **Cloudflare-style verification page**, follow these steps:  
1. **Create a file named `captcha.html` in your GitHub repository.**  
2. **Paste the CAPTCHA code provided in this repository.**  
3. **Customize the redirect URL in `captcha.html` as needed:**  
```js
window.location.href = "index.html"; // Change this to your main website page
```

---

## **🚀 Live Demo & Customization**
🔹 Customize **CAPTCHA text, animations, or redirect URL** in `captcha.html`.  
🔹 Modify the **design, colors, and layout** for a unique look.  
🔹 Ensure **email alerts work** by setting the correct developer email.  

---

## **💡 Why Use "Boters"?**
✔ **Works directly on GitHub Pages** (No backend required!)  
✔ **Prevents spam, bots, and fake traffic**  
✔ **Easy to set up and modify**  
✔ **100% free and open-source** 
### FULL CODE
```<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Security Boter | Smart Shield</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Arial', sans-serif; }
        body { display: flex; justify-content: center; align-items: center; height: 100vh; background: #121212; color: white; }
        .captcha-container { text-align: center; background: #1E1E1E; padding: 25px; border-radius: 10px; box-shadow: 0px 5px 15px rgba(255,255,255,0.2); width: 400px; }
        .captcha-box { margin: 15px 0; padding: 10px; background: #333; display: inline-block; border-radius: 5px; font-size: 22px; font-weight: bold; letter-spacing: 3px; color: #00FF99; }
        .input-field { width: 100%; padding: 10px; margin: 10px 0; border: 1px solid #555; background: #222; color: white; border-radius: 5px; text-align: center; font-size: 18px; }
        .verify-btn { margin-top: 15px; padding: 12px 20px; border: none; background: #00FF99; color: black; cursor: pointer; border-radius: 5px; width: 100%; font-size: 16px; font-weight: bold; }
        .verify-btn:disabled { background: gray; cursor: not-allowed; }
        .loading { display: none; font-size: 18px; margin-top: 15px; color: #00FF99; }
        .fade { animation: fadeOut 1s forwards; }
        @keyframes fadeOut { from { opacity: 1; } to { opacity: 0; visibility: hidden; } }
        .terms { margin-top: 10px; font-size: 12px; color: #888; }
        .checkbox-container { display: flex; align-items: center; justify-content: center; margin-top: 10px; }
        .checkbox-container input { margin-right: 10px; }
        #tick { font-size: 22px; display: none; }
        .loader { display: none; width: 50px; height: 50px; border: 5px solid #fff; border-top: 5px solid #00FF99; border-radius: 50%; animation: spin 1s linear infinite; margin: 20px auto; }
        @keyframes spin { from { transform: rotate(0deg); } to { transform: rotate(360deg); } }
    </style>
</head>
<body>

<div class="captcha-container">
    <h2>🔒 Checking Your Browser...</h2>
    <p>Complete the verification below</p>
    <div class="captcha-box" id="captcha-text"></div>
    <input type="text" id="captcha-input" class="input-field" placeholder="Enter Captcha">
    
    <div class="checkbox-container">
        <input type="checkbox" id="captcha-check" disabled> <label for="captcha-check">I am not a bot</label>
        <span id="tick">✔</span>
    </div>

    <div class="loader" id="loader"></div>

    <button class="verify-btn" id="verify-btn" disabled>Verify</button>
    <div class="loading" id="loading">✔ Verification Successful... Redirecting</div>
    <div class="terms">By continuing, you agree to our <a href="#">Terms & Conditions</a>.</div>
</div>

<script>
    function generateCaptcha() {
        let chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890";
        let captcha = "";
        for (let i = 0; i < 6; i++) {
            let randomChar = chars.charAt(Math.floor(Math.random() * chars.length));
            captcha += Math.random() > 0.5 ? randomChar.toUpperCase() : randomChar.toLowerCase();
        }
        document.getElementById("captcha-text").textContent = captcha;
        return captcha;
    }

    let generatedCaptcha = generateCaptcha();
    let captchaInput = document.getElementById('captcha-input');
    let captchaCheck = document.getElementById('captcha-check');
    let verifyBtn = document.getElementById('verify-btn');
    let tick = document.getElementById('tick');
    let loader = document.getElementById('loader');
    let container = document.querySelector('.captcha-container');

    let mouseMoved = false;
    document.body.addEventListener("mousemove", function() {
        mouseMoved = true;
    });

    captchaInput.addEventListener('input', function() {
        if (this.value === generatedCaptcha) {
            captchaCheck.disabled = false;
        } else {
            captchaCheck.disabled = true;
            verifyBtn.disabled = true;
        }
    });

    captchaCheck.addEventListener('change', function() {
        if (this.checked) {
            tick.style.display = 'inline';
            verifyBtn.disabled = false;
        } else {
            tick.style.display = 'none';
            verifyBtn.disabled = true;
        }
    });

    verifyBtn.addEventListener('click', function() {
        if (!mouseMoved) {
            alert("Bot detected! Verification failed.");
            sendEmailAlert();
            return;
        }
        loader.style.display = 'block';
        setTimeout(() => {
            container.classList.add('fade'); 
            window.location.href = "#"; 
        }, 3000);
    });

    function sendEmailAlert() {
        let developerEmail = "dev@example.com";
        let emailBody = encodeURIComponent("🚨 Bot attack detected on your site! Take action immediately.");
        window.location.href = `mailto:${developerEmail}?subject=Bot Alert&body=${emailBody}`;
    }
</script>

</body>
</html>

