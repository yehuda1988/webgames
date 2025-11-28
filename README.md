# webgames

אוסף משחקי דפדפן קלאסיים וכיפיים!

## 🚀 התקנה על שרת Apache2 (Home Lab)

### דרישות מקדימות:
- שרת Ubuntu/Debian עם Apache2 מותקן
- גישת SSH לשרת
- הרשאות sudo

### שלבי התקנה:

#### 1. התקן Apache2 (אם עדיין לא מותקן):
```bash
sudo apt update
sudo apt install apache2 -y
```

#### 2. הפעל והגדר Apache2:
```bash
sudo systemctl start apache2
sudo systemctl enable apache2
```

#### 3. העתק את קבצי המשחק לתיקיית האתר:
```bash
# צור תיקייה למשחקים
sudo mkdir -p /var/www/html/webgames

# העתק את הקבצים
sudo cp snakes-and-ladders.html /var/www/html/webgames/
sudo cp snake.html /var/www/html/webgames/

# הגדר הרשאות
sudo chown -R www-data:www-data /var/www/html/webgames
sudo chmod -R 755 /var/www/html/webgames
```

#### 4. (אופציונלי) צור עמוד אינדקס:
```bash
sudo nano /var/www/html/webgames/index.html
```

הוסף תוכן:
```html
<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
    <meta charset="UTF-8">
    <title>משחקי דפדפן</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 50px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }
        .container {
            background: white;
            padding: 40px;
            border-radius: 20px;
            max-width: 600px;
            margin: 0 auto;
        }
        h1 { color: #667eea; }
        a {
            display: block;
            margin: 20px 0;
            padding: 20px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            text-decoration: none;
            border-radius: 10px;
            font-size: 1.3em;
        }
        a:hover { opacity: 0.8; }
    </style>
</head>
<body>
    <div class="container">
        <h1>🎮 משחקי דפדפן</h1>
        <a href="snakes-and-ladders.html">🎲 סולמות ונחשים</a>
        <a href="snake.html">🐍 משחק הנחש</a>
    </div>
</body>
</html>
```

#### 5. גישה למשחקים:
פתח דפדפן והיכנס ל:
- **עמוד ראשי:** `http://YOUR_SERVER_IP/webgames/`
- **סולמות ונחשים:** `http://YOUR_SERVER_IP/webgames/snakes-and-ladders.html`
- **משחק הנחש:** `http://YOUR_SERVER_IP/webgames/snake.html`

### טיפים נוספים:

**בדיקת סטטוס Apache2:**
```bash
sudo systemctl status apache2
```

**צפייה בלוגים:**
```bash
sudo tail -f /var/log/apache2/access.log
sudo tail -f /var/log/apache2/error.log
```

**פתיחת פורט 80 בחומת אש (אם נדרש):**
```bash
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
```

---

## 🎲 סולמות ונחשים (Snakes and Ladders)

משחק לוח קלאסי עבור 2-4 שחקנים.

### תכונות:
- 👥 תמיכה ב-2-4 שחקנים
- 🎲 הטלת קוביה עם אנימציה
- 🪜 סולמות שמעלים אותך למעלה
- 🐍 נחשים שמורידים אותך למטה
- 🎨 עיצוב צבעוני ומושך
- 📊 מעקב אחר מיקום כל שחקן

### איך לשחק:
1. פתח את הקובץ `snakes-and-ladders.html` בדפדפן
2. בחר מספר שחקנים (2-4)
3. לחץ על "הטל קוביה" בתורך
4. השחקן הראשון שמגיע למשבצת 100 מנצח!

**טיפ:** נסה להגיע לסולמות ולהימנע מהנחשים!

---

## 🐍 משחק הנחש (Snake Game)

משחק סנייק קלאסי ונוסטלגי עם מכניקה פשוטה.

### תכונות:
- 🎮 שליטה באמצעות מקשי חצים
- 🏆 מעקב אחר ניקוד ושיא אישי
- ⏸️ אפשרות השהיה (מקש רווח)
- 🎨 עיצוב מודרני ומושך
- 💾 שמירת שיא המשחק

### איך לשחק:
1. פתח את הקובץ `snake.html` בדפדפן
2. השתמש במקשי החצים להזזת הנחש
3. אסוף את האוכל האדום כדי לצבור נקודות
4. הימנע מהתנגשות בקירות או בגוף שלך

**טיפ:** לחץ רווח כדי להשהות את המשחק!