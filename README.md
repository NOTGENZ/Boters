### **🚀 Boters - Cloudflare-Style CAPTCHA Shield for GitHub Pages**  

**Boters** is an advanced security shield that prevents bots from accessing your GitHub Pages site. It works like **Cloudflare's "Checking Your Browser"** page, ensuring only real users can enter while blocking automated bots.  

---

## **🌟 Features**
✅ **Pre-Website Verification** – Users must pass CAPTCHA before the main website loads.  
✅ **Mouse Movement Detection** – Bots that don’t move the mouse are automatically blocked.  
✅ **Hidden Honeypot Trap** – Invisible input field that only bots fill, leading to auto-failure.  
✅ **Checkbox & Delay Verification** – Ensures human interaction before proceeding.  
✅ **Loading Animation & Smooth Redirect** – A Cloudflare-style security experience.  
✅ **Email Alert for Bots** – If a bot is detected, an email alert is sent to the developer.  
✅ **100% Free & Open-Source** – Works directly on GitHub Pages without paid services.  

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

📢 **Need help or have suggestions? Open an issue on GitHub!**  

---

🚀 **Enjoy a bot-free, secure website with Boters!** 🔥
