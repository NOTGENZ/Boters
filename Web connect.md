### Web Connect - Boters
---
![shield_11918095](https://github.com/user-attachments/assets/897227d5-65d1-4c54-92f8-9e751181be9e)


 To connect Boters in a **web environment** other than GitHub Pages, follow these steps:

1. **Create the `index.html` file**:
   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>My Website</title>
       <script>
           if (!sessionStorage.getItem("captchaVerified")) {
               window.location.href = "captcha.html";
           }
       </script>
   </head>
   <body>
       <h1>Welcome to My Website</h1>
       <p>This is the main content of the site.</p>
   </body>
   </html>
   ```

2. **Create the `captcha.html` file**:
   Copy the `captcha.html` content from the Boters repository.

3. **Update Redirect in `captcha.html`**:
   Modify the redirect URL in `captcha.html` to point to your main website page:
   ```js
   window.location.href = "index.html"; // Change this to your main website page
   ```

4. **Set Up Email Alerts**:
   In `captcha.html`, update the email address to your actual email to receive bot alerts:
   ```js
   function sendEmailAlert() {
       let developerEmail = "your-email@example.com";
       let emailBody = encodeURIComponent("🚨 Bot detected on your site! Take action immediately.");
       window.location.href = `mailto:${developerEmail}?subject=Bot Alert&body=${emailBody}`;
   }
   ```

For a detailed guide and the full code, please refer to the Boters repository.

Here is the link & credit of icons:
[Boters - Web connection](https://github.com/NOTGENZ/Boters)
