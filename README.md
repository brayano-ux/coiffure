<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formation JavaScript Complète - ES6+</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: white;
            border-radius: 15px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            overflow: hidden;
        }

        header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 40px;
            text-align: center;
        }

        header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
        }

        header p {
            font-size: 1.2em;
            opacity: 0.9;
        }

        .nav {
            background: #2d3748;
            padding: 20px;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .nav ul {
            list-style: none;
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            justify-content: center;
        }

        .nav a {
            color: white;
            text-decoration: none;
            padding: 8px 16px;
            border-radius: 5px;
            transition: background 0.3s;
        }

        .nav a:hover {
            background: #667eea;
        }

        .content {
            padding: 40px;
        }

        section {
            margin-bottom: 60px;
            scroll-margin-top: 80px;
        }

        h2 {
            color: #667eea;
            font-size: 2em;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 3px solid #667eea;
        }

        h3 {
            color: #764ba2;
            font-size: 1.5em;
            margin: 30px 0 15px;
        }

        h4 {
            color: #2d3748;
            font-size: 1.2em;
            margin: 20px 0 10px;
        }

        p {
            margin-bottom: 15px;
            text-align: justify;
        }

        .info-box {
            background: #e6f3ff;
            border-left: 4px solid #667eea;
            padding: 20px;
            margin: 20px 0;
            border-radius: 5px;
        }

        .warning-box {
            background: #fff3cd;
            border-left: 4px solid #ffc107;
            padding: 20px;
            margin: 20px 0;
            border-radius: 5px;
        }

        .success-box {
            background: #d4edda;
            border-left: 4px solid #28a745;
            padding: 20px;
            margin: 20px 0;
            border-radius: 5px;
        }

        .code-block {
            background: #2d3748;
            color: #e2e8f0;
            padding: 20px;
            border-radius: 8px;
            margin: 20px 0;
            overflow-x: auto;
            font-family: 'Courier New', monospace;
            position: relative;
        }

        .code-block::before {
            content: 'JavaScript';
            position: absolute;
            top: 5px;
            right: 10px;
            background: #667eea;
            color: white;
            padding: 2px 10px;
            border-radius: 3px;
            font-size: 0.8em;
        }

        .code-inline {
            background: #f1f3f5;
            padding: 2px 8px;
            border-radius: 3px;
            font-family: 'Courier New', monospace;
            color: #c7254e;
        }

        .example {
            background: #f8f9fa;
            border: 2px solid #dee2e6;
            border-radius: 8px;
            padding: 20px;
            margin: 20px 0;
        }

        .example-title {
            font-weight: bold;
            color: #667eea;
            margin-bottom: 15px;
            font-size: 1.1em;
        }

        .demo-area {
            background: white;
            border: 2px dashed #667eea;
            border-radius: 5px;
            padding: 20px;
            margin: 15px 0;
            min-height: 60px;
        }

        button {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1em;
            transition: transform 0.2s, box-shadow 0.2s;
            margin: 5px;
        }

        button:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }

        button:active {
            transform: translateY(0);
        }

        input, select {
            padding: 10px;
            border: 2px solid #dee2e6;
            border-radius: 5px;
            font-size: 1em;
            margin: 5px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
        }

        table th {
            background: #667eea;
            color: white;
            padding: 12px;
            text-align: left;
        }

        table td {
            padding: 12px;
            border-bottom: 1px solid #dee2e6;
        }

        table tr:hover {
            background: #f8f9fa;
        }

        ul, ol {
            margin: 15px 0 15px 30px;
        }

        li {
            margin-bottom: 8px;
        }

        .grid-2 {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            margin: 20px 0;
        }

        footer {
            background: #2d3748;
            color: white;
            padding: 30px;
            text-align: center;
        }

        @media print {
            body {
                background: white;
                padding: 0;
            }
            .nav {
                position: static;
            }
            button {
                display: none;
            }
        }

        @media (max-width: 768px) {
            .grid-2 {
                grid-template-columns: 1fr;
            }
            header h1 {
                font-size: 1.8em;
            }
            .nav ul {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }

        .activation-container {
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            max-width: 500px;
            width: 100%;
            padding: 50px 40px;
            text-align: center;
            animation: slideIn 0.5s ease-out;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(-30px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .lock-icon {
            font-size: 4em;
            margin-bottom: 20px;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {

            0%,
            100% {
                transform: scale(1);
            }

            50% {
                transform: scale(1.1);
            }
        }

        h1 {
            color: #667eea;
            font-size: 2em;
            margin-bottom: 10px;
        }

        .subtitle {
            color: #666;
            margin-bottom: 40px;
            font-size: 1.1em;
        }

        .input-group {
            margin-bottom: 30px;
        }

        label {
            display: block;
            text-align: left;
            color: #333;
            font-weight: bold;
            margin-bottom: 10px;
            font-size: 1.1em;
        }

        input[type="text"] {
            width: 100%;
            padding: 15px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 1.1em;
            font-family: 'Courier New', monospace;
            text-align: center;
            text-transform: uppercase;
            letter-spacing: 2px;
            transition: all 0.3s;
        }

        input[type="text"]:focus {
            outline: none;
            border-color: #667eea;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }

        .activate-btn {
            width: 100%;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            padding: 18px;
            border-radius: 10px;
            font-size: 1.2em;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            margin-bottom: 20px;
        }

        .activate-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(102, 126, 234, 0.3);
        }

        .activate-btn:active {
            transform: translateY(0);
        }

        .message {
            padding: 15px;
            border-radius: 10px;
            margin-top: 20px;
            font-weight: bold;
            display: none;
            animation: fadeIn 0.3s;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
            }

            to {
                opacity: 1;
            }
        }

        .message.success {
            background: #d4edda;
            color: #155724;
            border: 2px solid #c3e6cb;
        }

        .message.warning {
            background: #fff3cd;
            color: #856404;
            border: 2px solid #ffeeba;
        }

        .message.error {
            background: #f8d7da;
            color: #721c24;
            border: 2px solid #f5c6cb;
        }

        .help-text {
            color: #999;
            font-size: 0.9em;
            margin-top: 30px;
            padding-top: 30px;
            border-top: 1px solid #e0e0e0;
        }

        .help-text a {
            color: #667eea;
            text-decoration: none;
            font-weight: bold;
        }

        .help-text a:hover {
            text-decoration: underline;
        }

        .loading {
            display: none;
            margin-top: 20px;
        }

        .loading-spinner {
            border: 4px solid #f3f3f3;
            border-top: 4px solid #667eea;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
            margin: 0 auto;
        }

        @keyframes spin {
            0% {
                transform: rotate(0deg);
            }

            100% {
                transform: rotate(360deg);
            }
        }

        .example-key {
            background: #f8f9fa;
            border: 1px dashed #ccc;
            padding: 10px;
            border-radius: 5px;
            font-family: 'Courier New', monospace;
            color: #667eea;
            margin-top: 10px;
            font-size: 0.9em;
        }

        .license-success-box {
            background: linear-gradient(135deg, #4caf50 0%, #45a049 100%);
            color: white;
            padding: 30px;
            border-radius: 15px;
            margin: 20px 0;
            text-align: center;
            display: none;
            animation: slideIn 0.5s ease-out;
        }

        .license-success-box h3 {
            color: white;
            margin-bottom: 15px;
            font-size: 1.5em;
        }

        .generated-key {
            background: rgba(255, 255, 255, 0.2);
            border: 2px solid white;
            padding: 20px;
            border-radius: 10px;
            font-family: 'Courier New', monospace;
            font-size: 1.5em;
            font-weight: bold;
            letter-spacing: 3px;
            margin: 20px 0;
            word-break: break-all;
        }

        .copy-key-btn {
            background: white;
            color: #4caf50;
            border: none;
            padding: 12px 30px;
            border-radius: 25px;
            font-size: 1.1em;
            font-weight: bold;
            cursor: pointer;
            margin: 10px 5px;
            transition: all 0.3s;
        }

        .copy-key-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }

        .copy-key-btn.copied {
            background: #2196f3;
            color: white;
        }

        .email-note {
            background: #fff3cd;
            border: 2px solid #ffc107;
            border-radius: 10px;
            padding: 15px;
            margin: 20px 0;
            color: #856404;
            font-size: 0.95em;
        }
    </style>

<html lang="fr">

    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Activation - Formation JavaScript</title>
    <!-- CinetPay SDK -->
    <script src="https://api.cinetpay.com/cdn/seamless/main.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }

        .activation-container {
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            max-width: 500px;
            width: 100%;
            padding: 50px 40px;
            text-align: center;
            animation: slideIn 0.5s ease-out;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(-30px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .lock-icon {
            font-size: 4em;
            margin-bottom: 20px;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {

            0%,
            100% {
                transform: scale(1);
            }

            50% {
                transform: scale(1.1);
            }
        }

        h1 {
            color: #667eea;
            font-size: 2em;
            margin-bottom: 10px;
        }

        .subtitle {
            color: #666;
            margin-bottom: 40px;
            font-size: 1.1em;
        }

        .input-group {
            margin-bottom: 30px;
        }

        label {
            display: block;
            text-align: left;
            color: #333;
            font-weight: bold;
            margin-bottom: 10px;
            font-size: 1.1em;
        }

        input[type="text"] {
            width: 100%;
            padding: 15px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 1.1em;
            font-family: 'Courier New', monospace;
            text-align: center;
            text-transform: uppercase;
            letter-spacing: 2px;
            transition: all 0.3s;
        }

        input[type="text"]:focus {
            outline: none;
            border-color: #667eea;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }

        .activate-btn {
            width: 100%;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            padding: 18px;
            border-radius: 10px;
            font-size: 1.2em;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            margin-bottom: 20px;
        }

        .activate-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(102, 126, 234, 0.3);
        }

        .activate-btn:active {
            transform: translateY(0);
        }

        .message {
            padding: 15px;
            border-radius: 10px;
            margin-top: 20px;
            font-weight: bold;
            display: none;
            animation: fadeIn 0.3s;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
            }

            to {
                opacity: 1;
            }
        }

        .message.success {
            background: #d4edda;
            color: #155724;
            border: 2px solid #c3e6cb;
        }

        .message.warning {
            background: #fff3cd;
            color: #856404;
            border: 2px solid #ffeeba;
        }

        .message.error {
            background: #f8d7da;
            color: #721c24;
            border: 2px solid #f5c6cb;
        }

        .help-text {
            color: #999;
            font-size: 0.9em;
            margin-top: 30px;
            padding-top: 30px;
            border-top: 1px solid #e0e0e0;
        }

        .help-text a {
            color: #667eea;
            text-decoration: none;
            font-weight: bold;
        }

        .help-text a:hover {
            text-decoration: underline;
        }

        .loading {
            display: none;
            margin-top: 20px;
        }

        .loading-spinner {
            border: 4px solid #f3f3f3;
            border-top: 4px solid #667eea;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
            margin: 0 auto;
        }

        @keyframes spin {
            0% {
                transform: rotate(0deg);
            }

            100% {
                transform: rotate(360deg);
            }
        }

        .example-key {
            background: #f8f9fa;
            border: 1px dashed #ccc;
            padding: 10px;
            border-radius: 5px;
            font-family: 'Courier New', monospace;
            color: #667eea;
            margin-top: 10px;
            font-size: 0.9em;
        }

        .license-success-box {
            background: linear-gradient(135deg, #4caf50 0%, #45a049 100%);
            color: white;
            padding: 30px;
            border-radius: 15px;
            margin: 20px 0;
            text-align: center;
            display: none;
            animation: slideIn 0.5s ease-out;
        }

        .license-success-box h3 {
            color: white;
            margin-bottom: 15px;
            font-size: 1.5em;
        }

        .generated-key {
            background: rgba(255, 255, 255, 0.2);
            border: 2px solid white;
            padding: 20px;
            border-radius: 10px;
            font-family: 'Courier New', monospace;
            font-size: 1.5em;
            font-weight: bold;
            letter-spacing: 3px;
            margin: 20px 0;
            word-break: break-all;
        }

        .copy-key-btn {
            background: white;
            color: #4caf50;
            border: none;
            padding: 12px 30px;
            border-radius: 25px;
            font-size: 1.1em;
            font-weight: bold;
            cursor: pointer;
            margin: 10px 5px;
            transition: all 0.3s;
        }

        .copy-key-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }

        .copy-key-btn.copied {
            background: #2196f3;
            color: white;
        }

        .email-note {
            background: #fff3cd;
            border: 2px solid #ffc107;
            border-radius: 10px;
            padding: 15px;
            margin: 20px 0;
            color: #856404;
            font-size: 0.95em;
        }
        /* Animation de transition */
.tous, .container {
    transition: opacity 0.3s ease-in-out;
}

/* Style pour l'écran d'authentification */
.activation-container {
    background: white;
    border-radius: 20px;
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
    max-width: 500px;
    width: 100%;
    padding: 50px 40px;
    text-align: center;
    animation: slideIn 0.5s ease-out;
}

@keyframes slideIn {
    from {
        opacity: 0;
        transform: translateY(-30px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* Message d'erreur */
.message {
    padding: 15px;
    border-radius: 10px;
    margin-top: 20px;
    font-weight: bold;
    display: none;
    animation: fadeIn 0.3s;
}

.message.error {
    background: #f8d7da;
    color: #721c24;
    border: 2px solid #f5c6cb;
}
    </style>
</head>

<body>
   <div class="tous" style="display: block;">
    <div class="activation-container">
        <div class="lock-icon">🔐</div>
        <h1 id="pageTitle">Activation de la Formation</h1>
        <p class="subtitle">Entrez votre clé de licence pour accéder à la formation complète</p>
        <div class="input-group">
            <label for="licenseKey">Clé de Licence</label>
            <input type="text" id="licenseKey" name="licenseKey" placeholder="XXXX-XXXX-XXXX-XXXX" maxlength="19" autocomplete="off">
        </div>
        <button type="submit" class="activate-btn" id="activateBtn">
            🚀 Activer Ma Formation
        </button>
    </div>
</div>
            <script>
               (function(){
    const CLE_ACCES = 'brayanoformation202';
    const ACT_KEY = 'formationJsActivated';
    const LICENSE_KEY = 'formationJsLicense';

    function readLocalDB() {
        try { 
            return JSON.parse(localStorage.getItem('licensesDB') || '{}'); 
        } catch(e) { 
            return {}; 
        }
    }

    function isExpired(iso) {
        if (!iso) return false;
        try { 
            return new Date(iso).getTime() <= Date.now(); 
        } catch(e) { 
            return false; 
        }
    }

    function isValidLicense(key) {
        if (!key) return false;
        key = key.trim();
        if (key === CLE_ACCES) return true;
        const db = readLocalDB();
        if (db && db[key] && db[key].actif) return true;
        
        // Vérifier la licence sauvegardée
        try {
            const saved = JSON.parse(localStorage.getItem(LICENSE_KEY) || '{}');
            if (saved && saved.licenseKey === key && !isExpired(saved.expiresAt)) {
                return true;
            }
        } catch(e) {}
        return false;
    }

    function saveActivation(key) {
        const now = Date.now();
        const expiresMs = 365 * 24 * 60 * 60 * 1000; // 1 an
        const activationData = {
            licenseKey: key,
            activatedAt: new Date(now).toISOString(),
            expiresAt: new Date(now + expiresMs).toISOString()
        };
        localStorage.setItem(LICENSE_KEY, JSON.stringify(activationData));
        localStorage.setItem(ACT_KEY, 'true');
    }

    function showContent() {
        // Afficher la formation
        const containers = document.querySelectorAll('.container');
        containers.forEach(c => {
            c.style.display = 'block';
        });
        
        // Masquer l'écran d'authentification
        const wrapper = document.querySelector('.tous');
        if (wrapper) wrapper.style.display = 'none';
        
        // Scroll en haut
        window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    function showAuthScreen() {
        // Afficher l'écran d'authentification
        const wrapper = document.querySelector('.tous');
        if (wrapper) wrapper.style.display = 'block';
        
        // Masquer la formation
        const containers = document.querySelectorAll('.container');
        containers.forEach(c => {
            c.style.display = 'none';
        });
    }

    // Vérification automatique au chargement
    document.addEventListener('DOMContentLoaded', function(){
        if (localStorage.getItem(ACT_KEY) === 'true') {
            try {
                const saved = JSON.parse(localStorage.getItem(LICENSE_KEY) || '{}');
                if (saved.licenseKey && !isExpired(saved.expiresAt) && isValidLicense(saved.licenseKey)) {
                    showContent();
                    return;
                } else {
                    // Licence expirée ou invalide
                    localStorage.removeItem(ACT_KEY);
                    localStorage.removeItem(LICENSE_KEY);
                    showAuthScreen();
                }
            } catch(e) { 
                console.warn('Erreur vérification licence:', e);
                showAuthScreen();
            }
        } else {
            showAuthScreen();
        }
    });

    // Gestion du bouton d'activation
    const activateBtn = document.getElementById('activateBtn');
    const licenseInput = document.getElementById('licenseKey');

    if (activateBtn && licenseInput) {
        activateBtn.addEventListener('click', function(){
            const key = (licenseInput.value || '').trim();
            
            if (!key) { 
                alert('Erreur: La clé de licence ne peut pas être vide.'); 
                licenseInput.focus(); 
                return; 
            }
            
            if (isValidLicense(key)) {
                saveActivation(key);
                alert('Félicitations! Votre formation a été activée avec succès.');
                showContent();
            } else {
                alert('Erreur: Clé de licence invalide. Veuillez réessayer.');
            }
        });

        // Activation avec la touche Entrée
        licenseInput.addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                activateBtn.click();
            }
        });
    }
})();
            </script>

           
</body>

</html>
    <div class="container" style="display: none;">
        <header>
            <h1>🚀 Formation JavaScript Complète</h1>
            <p>De débutant à expert - ES6+ et bonnes pratiques modernes</p>
        </header>

        <nav class="nav">
            <ul>
                <li><a href="#intro">Introduction</a></li>
                <li><a href="#bases">Bases</a></li>
                <li><a href="#structures">Structures de contrôle</a></li>
                <li><a href="#fonctions">Fonctions</a></li>
                <li><a href="#tableaux">Tableaux</a></li>
                <li><a href="#objets">Objets</a></li>
                <li><a href="#dom">DOM</a></li>
                <li><a href="#evenements">Événements</a></li>
                <li><a href="#poo">POO ES6</a></li>
                <li><a href="#async">Asynchrone</a></li>
            </ul>
        </nav>

        <div class="content">
            <!-- INTRODUCTION -->
            <section id="intro">
                <h2>📚 Introduction à JavaScript</h2>
                
                <h3>Qu'est-ce que JavaScript ?</h3>
                <p>
                    JavaScript est un langage de programmation interprété, principalement utilisé pour rendre les pages web interactives. 
                    Créé en 1995 par Brendan Eich, il est devenu l'un des langages les plus populaires au monde.
                </p>

                <div class="info-box">
                    <strong>💡 Points clés :</strong>
                    <ul>
                        <li>Langage interprété par le navigateur</li>
                        <li>Dynamique et non typé</li>
                        <li>Multi-paradigme (procédural, objet, fonctionnel)</li>
                        <li>ECMAScript 6 (ES6/ES2015) : révolution majeure</li>
                        <li>Utilisé côté client (navigateur) et serveur (Node.js)</li>
                    </ul>
                </div>

                <h3>Configuration de l'environnement</h3>
                <div class="grid-2">
                    <div>
                        <h4>Éditeur de code recommandé</h4>
                        <ul>
                            <li>Visual Studio Code</li>
                            <li>Sublime Text</li>
                            <li>WebStorm</li>
                        </ul>
                    </div>
                    <div>
                        <h4>Navigateur avec DevTools</h4>
                        <ul>
                            <li>Chrome (F12 ou Ctrl+Shift+I)</li>
                            <li>Firefox (F12 ou Ctrl+Shift+K)</li>
                            <li>Safari (Cmd+Option+I)</li>
                        </ul>
                    </div>
                </div>

                <h3>Intégrer JavaScript dans HTML</h3>
                
                <div class="code-block">// 1. Script inline (déconseillé)
&lt;button onclick="alert('Clic!')"&gt;Cliquer&lt;/button&gt;

// 2. Script interne
&lt;script&gt;
    console.log('Hello World!');
&lt;/script&gt;

// 3. Script externe (recommandé)
&lt;script src="script.js"&gt;&lt;/script&gt;</div>

                <div class="warning-box">
                    <strong>⚠️ Bonne pratique :</strong> Placez toujours vos balises &lt;script&gt; juste avant la fermeture de &lt;/body&gt; 
                    pour permettre au HTML de charger en premier.
                </div>
            </section>

            <!-- BASES -->
            <section id="bases">
                <h2>🎯 Les Bases du Langage</h2>

                <h3>Variables et Constantes</h3>
                
                <div class="code-block">// let : variable locale (bloc)
let nom = "Alice";
let age = 25;

// const : constante (ne peut pas être réassignée)
const PI = 3.14159;

// var : ancienne syntaxe (éviter)
var ancien = "obsolète";</div>

                <div class="warning-box">
                    <strong>⚠️ Important :</strong> Utilisez toujours <code class="code-inline">const</code> par défaut, 
                    et <code class="code-inline">let</code> uniquement si la valeur doit changer. N'utilisez jamais <code class="code-inline">var</code>.
                </div>

                <h3>Types de Données</h3>

                <table>
                    <thead>
                        <tr>
                            <th>Type</th>
                            <th>Description</th>
                            <th>Exemple</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td><strong>Number</strong></td>
                            <td>Nombres entiers et décimaux</td>
                            <td><code class="code-inline">42, 3.14, -7</code></td>
                        </tr>
                        <tr>
                            <td><strong>String</strong></td>
                            <td>Chaînes de caractères</td>
                            <td><code class="code-inline">"Hello", 'World'</code></td>
                        </tr>
                        <tr>
                            <td><strong>Boolean</strong></td>
                            <td>Vrai ou faux</td>
                            <td><code class="code-inline">true, false</code></td>
                        </tr>
                        <tr>
                            <td><strong>Undefined</strong></td>
                            <td>Variable non initialisée</td>
                            <td><code class="code-inline">undefined</code></td>
                        </tr>
                        <tr>
                            <td><strong>Null</strong></td>
                            <td>Valeur nulle intentionnelle</td>
                            <td><code class="code-inline">null</code></td>
                        </tr>
                        <tr>
                            <td><strong>Object</strong></td>
                            <td>Collections de données</td>
                            <td><code class="code-inline">{}, []</code></td>
                        </tr>
                    </tbody>
                </table>

                <div class="example">
                    <div class="example-title">📋 Exemple pratique : typeof</div>
                    <div class="code-block">console.log(typeof 42);        // "number"
console.log(typeof "Hello");   // "string"
console.log(typeof true);      // "boolean"
console.log(typeof {});        // "object"
console.log(typeof []);        // "object"
console.log(typeof null);      // "object" (bug historique!)</div>
                    <button onclick="demoTypeof()">Tester typeof</button>
                    <div id="demo-typeof" class="demo-area"></div>
                </div>

                <h3>Opérateurs</h3>

                <h4>Opérateurs Arithmétiques</h4>
                <div class="code-block">let a = 10, b = 3;

console.log(a + b);   // 13 (addition)
console.log(a - b);   // 7  (soustraction)
console.log(a * b);   // 30 (multiplication)
console.log(a / b);   // 3.333... (division)
console.log(a % b);   // 1  (modulo - reste)
console.log(a ** b);  // 1000 (puissance)</div>

                <h4>Opérateurs de Comparaison</h4>
                <div class="code-block">// Égalité faible (avec conversion de type)
console.log(5 == "5");    // true

// Égalité stricte (sans conversion)
console.log(5 === "5");   // false

// Inégalité
console.log(5 != "6");    // true
console.log(5 !== "5");   // true

// Comparaisons
console.log(5 > 3);       // true
console.log(5 <= 5);      // true</div>

                <div class="success-box">
                    <strong>✅ Bonne pratique :</strong> Utilisez toujours <code class="code-inline">===</code> et 
                    <code class="code-inline">!==</code> pour éviter les conversions implicites.
                </div>

                <h3>Template Literals (ES6)</h3>
                <div class="code-block">const nom = "Alice";
const age = 25;

// Ancienne méthode
console.log("Je m'appelle " + nom + " et j'ai " + age + " ans");

// Template literals (recommandé)
console.log(`Je m'appelle ${nom} et j'ai ${age} ans`);

// Multi-lignes
const texte = `
    Ceci est un texte
    sur plusieurs lignes
    avec ${nom}
`;</div>

                <div class="example">
                    <div class="example-title">📋 Calculatrice Simple</div>
                    <input type="number" id="calc-a" placeholder="Nombre 1" value="10">
                    <select id="calc-op">
                        <option value="+">+</option>
                        <option value="-">-</option>
                        <option value="*">×</option>
                        <option value="/">÷</option>
                    </select>
                    <input type="number" id="calc-b" placeholder="Nombre 2" value="5">
                    <button onclick="calculer()">Calculer</button>
                    <div id="calc-result" class="demo-area"></div>
                </div>
            </section>

            <!-- STRUCTURES DE CONTRÔLE -->
            <section id="structures">
                <h2>🔀 Structures de Contrôle</h2>

                <h3>Conditions : if / else if / else</h3>
                <div class="code-block">const age = 18;

if (age < 13) {
    console.log("Enfant");
} else if (age < 18) {
    console.log("Adolescent");
} else if (age < 60) {
    console.log("Adulte");
} else {
    console.log("Senior");
}</div>

                <h3>Opérateur Ternaire</h3>
                <div class="code-block">const age = 20;
const statut = age >= 18 ? "Majeur" : "Mineur";

// Équivalent à :
// let statut;
// if (age >= 18) {
//     statut = "Majeur";
// } else {
//     statut = "Mineur";
// }</div>

                <h3>Switch</h3>
                <div class="code-block">const jour = 3;
let nomJour;

switch(jour) {
    case 1:
        nomJour = "Lundi";
        break;
    case 2:
        nomJour = "Mardi";
        break;
    case 3:
        nomJour = "Mercredi";
        break;
    default:
        nomJour = "Autre jour";
}</div>

                <div class="example">
                    <div class="example-title">📋 Vérification d'âge</div>
                    <input type="number" id="age-input" placeholder="Entrez votre âge" value="25">
                    <button onclick="verifierAge()">Vérifier</button>
                    <div id="age-result" class="demo-area"></div>
                </div>

                <h3>Boucles</h3>

                <h4>Boucle For</h4>
                <div class="code-block">// Boucle classique
for (let i = 0; i < 5; i++) {
    console.log(`Itération ${i}`);
}

// Parcourir un tableau
const fruits = ["Pomme", "Banane", "Orange"];
for (let i = 0; i < fruits.length; i++) {
    console.log(fruits[i]);
}</div>

                <h4>Boucle While</h4>
                <div class="code-block">let compteur = 0;

while (compteur < 5) {
    console.log(compteur);
    compteur++;
}

// Do...while (exécute au moins une fois)
do {
    console.log("Exécuté au moins une fois");
} while (false);</div>

                <h4>For...of et For...in (ES6)</h4>
                <div class="code-block">const fruits = ["Pomme", "Banane", "Orange"];

// for...of : parcourt les valeurs
for (const fruit of fruits) {
    console.log(fruit);
}

// for...in : parcourt les indices/clés
for (const index in fruits) {
    console.log(`${index}: ${fruits[index]}`);
}</div>

                <div class="example">
                    <div class="example-title">📋 Table de Multiplication</div>
                    <input type="number" id="table-num" placeholder="Nombre" value="7" min="1" max="20">
                    <button onclick="afficherTable()">Générer la table</button>
                    <div id="table-result" class="demo-area"></div>
                </div>
            </section>

            <!-- FONCTIONS -->
            <section id="fonctions">
                <h2>⚙️ Fonctions</h2>

                <h3>Déclaration de Fonction</h3>
                <div class="code-block">// Déclaration classique
function saluer(nom) {
    return `Bonjour ${nom}!`;
}

console.log(saluer("Alice")); // "Bonjour Alice!"

// Fonction avec valeur par défaut (ES6)
function direBonjour(nom = "Invité") {
    return `Bonjour ${nom}!`;
}

console.log(direBonjour());        // "Bonjour Invité!"
console.log(direBonjour("Bob"));   // "Bonjour Bob!"</div>

                <h3>Expression de Fonction</h3>
                <div class="code-block">const addition = function(a, b) {
    return a + b;
};

console.log(addition(5, 3)); // 8</div>

                <h3>Fonctions Flèches (Arrow Functions ES6)</h3>
                <div class="code-block">// Syntaxe complète
const multiplier = (a, b) => {
    return a * b;
};

// Syntaxe courte (return implicite)
const multiplier2 = (a, b) => a * b;

// Un seul paramètre (parenthèses optionnelles)
const carre = x => x * x;

// Pas de paramètre
const direBonjour = () => "Bonjour!";

console.log(multiplier(4, 5));  // 20
console.log(carre(5));          // 25</div>

                <div class="info-box">
                    <strong>💡 Différence importante :</strong> Les fonctions flèches n'ont pas leur propre <code class="code-inline">this</code>. 
                    Elles héritent du <code class="code-inline">this</code> du contexte parent.
                </div>

                <h3>Fonctions d'Ordre Supérieur</h3>
                <div class="code-block">// Fonction qui retourne une fonction
function creerMultiplicateur(facteur) {
    return function(nombre) {
        return nombre * facteur;
    };
}

const doubler = creerMultiplicateur(2);
const tripler = creerMultiplicateur(3);

console.log(doubler(5));  // 10
console.log(tripler(5));  // 15

// Version avec arrow function
const creerMultiplicateur2 = facteur => nombre => nombre * facteur;</div>

                <h3>Rest Parameters et Spread Operator (ES6)</h3>
                <div class="code-block">// Rest parameters (...args)
function somme(...nombres) {
    return nombres.reduce((total, n) => total + n, 0);
}

console.log(somme(1, 2, 3, 4, 5)); // 15

// Spread operator
const nombres = [1, 2, 3];
const autresNombres = [4, 5, 6];
const tous = [...nombres, ...autresNombres];
console.log(tous); // [1, 2, 3, 4, 5, 6]</div>

                <div class="example">
                    <div class="example-title">📋 Calculateur de Moyenne</div>
                    <input type="text" id="notes-input" placeholder="Entrez des notes (séparées par des virgules)" value="15, 12, 18, 14">
                    <button onclick="calculerMoyenne()">Calculer la moyenne</button>
                    <div id="moyenne-result" class="demo-area"></div>
                </div>

                <h3>Scope (Portée des Variables)</h3>
                <div class="code-block">const global = "Je suis globale";

function exemple() {
    const locale = "Je suis locale";
    console.log(global);  // Accessible
    console.log(locale);  // Accessible
    
    if (true) {
        const bloc = "Je suis dans le bloc";
        console.log(bloc);  // Accessible
    }
    
    // console.log(bloc);  // Erreur! Pas accessible
}

// console.log(locale);  // Erreur! Pas accessible</div>
            </section>

            <!-- TABLEAUX -->
            <section id="tableaux">
                <h2>📊 Tableaux (Arrays)</h2>

                <h3>Création et Manipulation de Base</h3>
                <div class="code-block">// Création
const fruits = ["Pomme", "Banane", "Orange"];
const nombres = [1, 2, 3, 4, 5];
const mixte = [1, "texte", true, null, {nom: "objet"}];

// Accès aux éléments
console.log(fruits[0]);        // "Pomme"
console.log(fruits.length);    // 3

// Modification
fruits[1] = "Fraise";
console.log(fruits);  // ["Pomme", "Fraise", "Orange"]</div>

                <h3>Méthodes Essentielles</h3>

                <h4>Ajouter / Supprimer des Éléments</h4>
                <div class="code-block">const arr = [1, 2, 3];

// Ajouter à la fin
arr.push(4);           // [1, 2, 3, 4]

// Retirer de la fin
arr.pop();             // [1, 2, 3]

// Ajouter au début
arr.unshift(0);        // [0, 1, 2, 3]

// Retirer du début
arr.shift();           // [1, 2, 3]

// Ajouter/supprimer au milieu
arr.splice(1, 1, 5, 6);  // [1, 5, 6, 3]</div>

                <h4>Méthodes de Recherche</h4>
                <div class="code-block">const fruits = ["Pomme", "Banane", "Orange", "Banane"];

// indexOf - premier index
fruits.indexOf("Banane");     // 1

// lastIndexOf - dernier index
fruits.lastIndexOf("Banane"); // 3

// includes - vérifier présence
fruits.includes("Orange");    // true

// find - premier élément qui satisfait
const nombres = [5, 12, 8, 130, 44];
const trouve = nombres.find(n => n > 10);
console.log(trouve);  // 12

// findIndex - index du premier élément
const index = nombres.findIndex(n => n > 10);
console.log(index);   // 1</div>

                <h3>Méthodes Modernes (ES6+)</h3>

                <h4>map() - Transformer chaque élément</h4>
                <div class="code-block">const nombres = [1, 2, 3, 4, 5];

// Doubler chaque nombre
const doubles = nombres.map(n => n * 2);
console.log(doubles);  // [2, 4, 6, 8, 10]

// Créer des objets
const personnes = ["Alice", "Bob", "Charlie"];
const objets = personnes.map((nom, index) => ({
    id: index + 1,
    nom: nom
}));
console.log(objets);
// [{id: 1, nom: "Alice"}, {id: 2, nom: "Bob"}, ...]</div>

                <h4>filter() - Filtrer les éléments</h4>
                <div class="code-block">const nombres = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

// Garder seulement les pairs
const pairs = nombres.filter(n => n % 2 === 0);
console.log(pairs);  // [2, 4, 6, 8, 10]

// Filtrer les étudiants admis
const etudiants = [
    {nom: "Alice", note: 15},
    {nom: "Bob", note: 8},
    {nom: "Charlie", note: 12}
];
const admis = etudiants.filter(e => e.note >= 10);
console.log(admis);</div>

                <h4>reduce() - Réduire à une valeur</h4>
                <div class="code-block">const nombres = [1, 2, 3, 4, 5];

// Somme
const somme = nombres.reduce((acc, n) => acc + n, 0);
console.log(somme);  // 15

// Produit
const produit = nombres.reduce((acc, n) => acc * n, 1);
console.log(produit);  // 120

// Compter occurrences
const fruits = ["pomme", "banane", "pomme", "orange", "banane", "pomme"];
const compte = fruits.reduce((acc, fruit) => {
    acc[fruit] = (acc[fruit] || 0) + 1;
    return acc;
}, {});
console.log(compte);  // {pomme: 3, banane: 2, orange: 1}</div>

                <h4>forEach() - Itérer sur chaque élément</h4>
                <div class="code-block">const fruits = ["Pomme", "Banane", "Orange"];

fruits.forEach((fruit, index) => {
    console.log(`${index + 1}. ${fruit}`);
});
// 1. Pomme
// 2. Banane
// 3. Orange</div>

                <h4>some() et every() - Tests sur tableau</h4>
                <div class="code-block">const nombres = [1, 2, 3, 4, 5];

// some() - au moins un élément satisfait
const aUnPair = nombres.some(n => n % 2 === 0);
console.log(aUnPair);  // true

// every() - tous les éléments satisfont
const tousPositifs = nombres.every(n => n > 0);
console.log(tousPositifs);  // true</div>

                <h4>sort() - Trier un tableau</h4>
                <div class="code-block">// Tri alphabétique (par défaut)
const fruits = ["Orange", "Pomme", "Banane"];
fruits.sort();
console.log(fruits);  // ["Banane", "Orange", "Pomme"]

// Tri numérique
const nombres = [40, 100, 1, 5, 25, 10];
nombres.sort((a, b) => a - b);  // Croissant
console.log(nombres);  // [1, 5, 10, 25, 40, 100]

// Tri décroissant
nombres.sort((a, b) => b - a);
console.log(nombres);  // [100, 40, 25, 10, 5, 1]

// Tri d'objets
const personnes = [
    {nom: "Charlie", age: 30},
    {nom: "Alice", age: 25},
    {nom: "Bob", age: 35}
];
personnes.sort((a, b) => a.age - b.age);
console.log(personnes);</div>

                <div class="example">
                    <div class="example-title">📋 Gestionnaire de Tâches</div>
                    <input type="text" id="tache-input" placeholder="Nouvelle tâche">
                    <button onclick="ajouterTache()">Ajouter</button>
                    <button onclick="filtrerTaches()">Filtrer (A-M)</button>
                    <button onclick="trierTaches()">Trier A-Z</button>
                    <button onclick="viderTaches()">Vider</button>
                    <div id="taches-result" class="demo-area"></div>
                </div>

                <h3>Destructuration de Tableau (ES6)</h3>
                <div class="code-block">// Destructuration simple
const [premier, deuxieme, troisieme] = [1, 2, 3];
console.log(premier);  // 1
console.log(deuxieme); // 2

// Ignorer des éléments
const [a, , c] = [1, 2, 3];
console.log(c);  // 3

// Rest operator
const [first, ...rest] = [1, 2, 3, 4, 5];
console.log(first);  // 1
console.log(rest);   // [2, 3, 4, 5]

// Échange de variables
let x = 1, y = 2;
[x, y] = [y, x];
console.log(x, y);  // 2, 1</div>
            </section>

            <!-- OBJETS -->
            <section id="objets">
                <h2>🎁 Objets (Objects)</h2>

                <h3>Création d'Objets</h3>
                <div class="code-block">// Objet littéral
const personne = {
    nom: "Alice",
    age: 25,
    ville: "Paris",
    estEtudiant: true
};

// Accès aux propriétés
console.log(personne.nom);        // "Alice"
console.log(personne["age"]);     // 25

// Modification
personne.age = 26;
personne["ville"] = "Lyon";

// Ajout de propriété
personne.email = "alice@example.com";

// Suppression
delete personne.estEtudiant;</div>

                <h3>Méthodes d'Objet</h3>
                <div class="code-block">const calculatrice = {
    valeur: 0,
    
    // Méthode classique
    ajouter: function(n) {
        this.valeur += n;
        return this;  // Chaînage
    },
    
    // Syntaxe courte (ES6)
    soustraire(n) {
        this.valeur -= n;
        return this;
    },
    
    multiplier(n) {
        this.valeur *= n;
        return this;
    },
    
    resultat() {
        return this.valeur;
    }
};

// Chaînage de méthodes
const result = calculatrice
    .ajouter(10)
    .multiplier(2)
    .soustraire(5)
    .resultat();
console.log(result);  // 15</div>

                <h3>Propriétés Calculées (ES6)</h3>
                <div class="code-block">const cle = "couleur";
const valeur = "bleu";

const objet = {
    [cle]: valeur,           // couleur: "bleu"
    ["age" + "Max"]: 100,    // ageMax: 100
    ["total" + (1 + 1)]: 42  // total2: 42
};

console.log(objet.couleur);  // "bleu"
console.log(objet.ageMax);   // 100</div>

                <h3>Destructuration d'Objet (ES6)</h3>
                <div class="code-block">const personne = {
    nom: "Alice",
    age: 25,
    ville: "Paris",
    pays: "France"
};

// Destructuration simple
const {nom, age} = personne;
console.log(nom);  // "Alice"
console.log(age);  // 25

// Renommer les variables
const {nom: prenom, age: annees} = personne;
console.log(prenom);  // "Alice"

// Valeur par défaut
const {profession = "Inconnu"} = personne;
console.log(profession);  // "Inconnu"

// Rest operator
const {ville, ...reste} = personne;
console.log(reste);  // {nom: "Alice", age: 25, pays: "France"}</div>

                <h3>Spread Operator pour Objets (ES6)</h3>
                <div class="code-block">const obj1 = {a: 1, b: 2};
const obj2 = {c: 3, d: 4};

// Fusion d'objets
const fusion = {...obj1, ...obj2};
console.log(fusion);  // {a: 1, b: 2, c: 3, d: 4}

// Copie avec modification
const personne = {nom: "Alice", age: 25};
const personneModifiee = {...personne, age: 26, ville: "Paris"};
console.log(personneModifiee);
// {nom: "Alice", age: 26, ville: "Paris"}</div>

                <h3>Méthodes Object Utiles</h3>
                <div class="code-block">const personne = {
    nom: "Alice",
    age: 25,
    ville: "Paris"
};

// Object.keys() - Tableau des clés
console.log(Object.keys(personne));
// ["nom", "age", "ville"]

// Object.values() - Tableau des valeurs
console.log(Object.values(personne));
// ["Alice", 25, "Paris"]

// Object.entries() - Tableau de paires [clé, valeur]
console.log(Object.entries(personne));
// [["nom", "Alice"], ["age", 25], ["ville", "Paris"]]

// Object.assign() - Copie d'objet
const copie = Object.assign({}, personne);

// Object.freeze() - Rendre immuable
Object.freeze(personne);
// personne.age = 30;  // Ne fait rien en mode strict</div>

                <h3>JSON - JavaScript Object Notation</h3>
                <div class="code-block">const personne = {
    nom: "Alice",
    age: 25,
    hobbies: ["lecture", "sport"]
};

// Convertir en JSON (string)
const json = JSON.stringify(personne);
console.log(json);
// '{"nom":"Alice","age":25,"hobbies":["lecture","sport"]}'

// Parser le JSON
const parsed = JSON.parse(json);
console.log(parsed.nom);  // "Alice"

// Avec indentation (lisible)
const jsonFormate = JSON.stringify(personne, null, 2);
console.log(jsonFormate);</div>

                <div class="example">
                    <div class="example-title">📋 Carnet d'Adresses</div>
                    <input type="text" id="contact-nom" placeholder="Nom">
                    <input type="email" id="contact-email" placeholder="Email">
                    <input type="tel" id="contact-tel" placeholder="Téléphone">
                    <button onclick="ajouterContact()">Ajouter Contact</button>
                    <div id="contacts-result" class="demo-area"></div>
                </div>
            </section>

            <!-- DOM -->
            <section id="dom">
                <h2>🌳 DOM - Document Object Model</h2>

                <h3>Qu'est-ce que le DOM ?</h3>
                <p>
                    Le DOM est une interface de programmation qui représente la structure HTML d'une page comme un arbre d'objets.
                    JavaScript peut manipuler cet arbre pour modifier dynamiquement le contenu, la structure et le style de la page.
                </p>

                <h3>Sélectionner des Éléments</h3>
                <div class="code-block">// Par ID (retourne un élément)
const element = document.getElementById('monId');

// Par classe (retourne une HTMLCollection)
const elements = document.getElementsByClassName('maClasse');

// Par balise (retourne une HTMLCollection)
const paragraphes = document.getElementsByTagName('p');

// Query Selector (CSS) - moderne et recommandé
const premier = document.querySelector('.maClasse');  // Premier élément
const tous = document.querySelectorAll('.maClasse');  // NodeList de tous

// Sélecteurs CSS avancés
document.querySelector('#monId .enfant');
document.querySelectorAll('div > p');
document.querySelector('[data-id="123"]');</div>

                <div class="info-box">
                    <strong>💡 Bonne pratique :</strong> Utilisez <code class="code-inline">querySelector</code> et 
                    <code class="code-inline">querySelectorAll</code> pour une syntaxe moderne et cohérente.
                </div>

                <h3>Manipuler le Contenu</h3>
                <div class="code-block">const element = document.querySelector('#monElement');

// innerHTML - HTML complet (attention XSS!)
element.innerHTML = '&lt;strong&gt;Texte en gras&lt;/strong&gt;';

// textContent - Texte uniquement (sécurisé)
element.textContent = 'Texte simple';

// innerText - Texte visible (tient compte du CSS)
element.innerText = 'Texte visible';

// Lire le contenu
const contenu = element.textContent;</div>

                <h3>Manipuler les Attributs</h3>
                <div class="code-block">const lien = document.querySelector('a');

// getAttribute / setAttribute
lien.setAttribute('href', 'https://example.com');
const url = lien.getAttribute('href');

// Propriétés directes
lien.href = 'https://example.com';
lien.target = '_blank';

// Attributs data-*
const element = document.querySelector('[data-id]');
element.dataset.id = '123';
element.dataset.userName = 'Alice';
// &lt;div data-id="123" data-user-name="Alice"&gt;

console.log(element.dataset.id);       // "123"
console.log(element.dataset.userName); // "Alice"</div>

                <h3>Manipuler les Classes CSS</h3>
                <div class="code-block">const element = document.querySelector('.monElement');

// classList - API moderne
element.classList.add('nouvelle-classe');
element.classList.remove('ancienne-classe');
element.classList.toggle('actif');  // Ajoute si absent, retire si présent
element.classList.contains('actif'); // true ou false

// Plusieurs classes
element.classList.add('classe1', 'classe2', 'classe3');

// className - ancienne méthode (remplace tout)
element.className = 'classe1 classe2';</div>

                <h3>Manipuler les Styles</h3>
                <div class="code-block">const element = document.querySelector('.monElement');

// Styles inline
element.style.color = 'red';
element.style.backgroundColor = 'blue';
element.style.fontSize = '20px';

// CamelCase pour les propriétés CSS
element.style.borderRadius = '10px';

// Lire les styles
const couleur = element.style.color;

// getComputedStyle - styles calculés finaux
const styles = window.getComputedStyle(element);
const largeur = styles.width;</div>

                <h3>Créer et Ajouter des Éléments</h3>
                <div class="code-block">// Créer un élément
const div = document.createElement('div');
div.textContent = 'Nouveau div';
div.classList.add('ma-classe');

// Ajouter à la fin d'un parent
const parent = document.querySelector('#container');
parent.appendChild(div);

// Ajouter au début
parent.insertBefore(div, parent.firstChild);

// Méthodes modernes (ES6)
parent.append(div);           // Ajoute à la fin
parent.prepend(div);          // Ajoute au début
parent.before(div);           // Insère avant le parent
parent.after(div);            // Insère après le parent

// Supprimer un élément
div.remove();

// Remplacer un élément
const nouveau = document.createElement('span');
div.replaceWith(nouveau);</div>

                <h3>Naviguer dans le DOM</h3>
                <div class="code-block">const element = document.querySelector('.monElement');

// Parents
element.parentElement;          // Parent direct
element.closest('.classe');     // Premier ancêtre correspondant

// Enfants
element.children;               // HTMLCollection des enfants
element.firstElementChild;      // Premier enfant
element.lastElementChild;       // Dernier enfant
element.childElementCount;      // Nombre d'enfants

// Frères et sœurs
element.nextElementSibling;     // Élément suivant
element.previousElementSibling; // Élément précédent</div>

                <div class="example">
                    <div class="example-title">📋 Manipulateur DOM Interactif</div>
                    <div id="demo-dom-box" style="padding: 20px; background: #f0f0f0; border-radius: 5px; margin: 10px 0;">
                        <p id="demo-dom-text">Texte à modifier</p>
                    </div>
                    <input type="text" id="dom-input" placeholder="Nouveau texte" value="Bonjour le DOM!">
                    <button onclick="changerTexte()">Changer Texte</button>
                    <button onclick="toggleClasse()">Toggle Classe</button>
                    <button onclick="changerCouleur()">Changer Couleur</button>
                    <button onclick="ajouterElement()">Ajouter Élément</button>
                </div>
            </section>

            <!-- ÉVÉNEMENTS -->
            <section id="evenements">
                <h2>⚡ Gestion des Événements</h2>

                <h3>addEventListener - Méthode Moderne</h3>
                <div class="code-block">const bouton = document.querySelector('#monBouton');

// Ajouter un écouteur d'événement
bouton.addEventListener('click', function(event) {
    console.log('Bouton cliqué!');
    console.log('Élément:', event.target);
});

// Avec fonction flèche
bouton.addEventListener('click', (e) => {
    console.log('Clic!');
});

// Fonction nommée (pour pouvoir la retirer)
function gererClic(e) {
    console.log('Clic géré');
}

bouton.addEventListener('click', gererClic);

// Retirer l'écouteur
bouton.removeEventListener('click', gererClic);</div>

                <h3>Événements Courants</h3>

                <h4>Événements de Souris</h4>
                <div class="code-block">element.addEventListener('click', e => {});      // Clic
element.addEventListener('dblclick', e => {});   // Double-clic
element.addEventListener('mouseenter', e => {}); // Survol (entre)
element.addEventListener('mouseleave', e => {}); // Survol (sort)
element.addEventListener('mousemove', e => {});  // Mouvement souris
element.addEventListener('mousedown', e => {});  // Bouton pressé
element.addEventListener('mouseup', e => {});    // Bouton relâché</div>

                <h4>Événements de Clavier</h4>
                <div class="code-block">input.addEventListener('keydown', e => {
    console.log('Touche pressée:', e.key);
});

input.addEventListener('keyup', e => {
    console.log('Touche relâchée:', e.key);
});

input.addEventListener('keypress', e => {
    console.log('Caractère:', e.key);
});</div>

                <h4>Événements de Formulaire</h4>
                <div class="code-block">const input = document.querySelector('input');
const form = document.querySelector('form');

input.addEventListener('input', e => {
    console.log('Valeur:', e.target.value);
});

input.addEventListener('change', e => {
    console.log('Changé:', e.target.value);
});

input.addEventListener('focus', e => {
    console.log('Focus');
});

input.addEventListener('blur', e => {
    console.log('Perte de focus');
});

form.addEventListener('submit', e => {
    e.preventDefault();  // Empêche l'envoi du formulaire
    console.log('Formulaire soumis');
});</div>

                <h3>Objet Event</h3>
                <div class="code-block">element.addEventListener('click', (event) => {
    // Élément qui a déclenché l'événement
    console.log(event.target);
    
    // Élément sur lequel l'écouteur est attaché
    console.log(event.currentTarget);
    
    // Type d'événement
    console.log(event.type);  // "click"
    
    // Position de la souris
    console.log(event.clientX, event.clientY);
    
    // Touches modifcatrices
    console.log(event.ctrlKey, event.shiftKey, event.altKey);
    
    // Empêcher le comportement par défaut
    event.preventDefault();
    
    // Arrêter la propagation
    event.stopPropagation();
});</div>

                <h3>Propagation des Événements</h3>
                <div class="code-block">// HTML: &lt;div id="parent"&gt;&lt;button id="enfant"&gt;Clic&lt;/button&gt;&lt;/div&gt;

const parent = document.querySelector('#parent');
const enfant = document.querySelector('#enfant');

// Phase de capture (rare)
parent.addEventListener('click', () => {
    console.log('Parent - capture');
}, true);

// Phase de bouillonnement (par défaut)
parent.addEventListener('click', () => {
    console.log('Parent - bouillonnement');
});

enfant.addEventListener('click', (e) => {
    console.log('Enfant cliqué');
    // e.stopPropagation();  // Arrête la propagation
});

// Ordre: Capture parent -> Enfant -> Bouillonnement parent</div>

                <h3>Délégation d'Événements</h3>
                <div class="code-block">// Au lieu d'ajouter un écouteur sur chaque élément
const liste = document.querySelector('#maListe');

liste.addEventListener('click', (e) => {
    // Vérifier si c'est un élément &lt;li&gt; qui a été cliqué
    if (e.target.tagName === 'LI') {
        console.log('Item cliqué:', e.target.textContent);
        e.target.classList.toggle('actif');
    }
});

// Avantages:
// - Un seul écouteur au lieu de plusieurs
// - Fonctionne pour les éléments ajoutés dynamiquement</div>

                <div class="example">
                    <div class="example-title">📋 Compteur de Clics Interactif</div>
                    <div id="compteur-display" style="font-size: 2em; text-align: center; margin: 20px 0;">0</div>
                    <button onclick="incrementerCompteur()">+1</button>
                    <button onclick="decrementerCompteur()">-1</button>
                    <button onclick="resetCompteur()">Reset</button>
                    <button onclick="multiplierCompteur()">×2</button>
                </div>

                <div class="example">
                    <div class="example-title">📋 Liste Interactive avec Délégation</div>
                    <input type="text" id="item-input" placeholder="Nouvel item">
                    <button onclick="ajouterItem()">Ajouter</button>
                    <ul id="liste-interactive" style="list-style: none; padding: 0; margin: 15px 0;"></ul>
                </div>
            </section>

            <!-- POO ES6 -->
            <section id="poo">
                <h2>🎓 Programmation Orientée Objet (ES6)</h2>

                <h3>Classes (ES6)</h3>
                <div class="code-block">class Personne {
    // Constructeur
    constructor(nom, age) {
        this.nom = nom;
        this.age = age;
    }
    
    // Méthode
    sePresenter() {
        return `Je m'appelle ${this.nom} et j'ai ${this.age} ans.`;
    }
    
    // Méthode
    vieillir() {
        this.age++;
    }
    
    // Getter
    get majeur() {
        return this.age >= 18;
    }
    
    // Setter
    set anniversaire(date) {
        const annee = new Date(date).getFullYear();
        this.age = new Date().getFullYear() - annee;
    }
    
    // Méthode statique
    static creerEnfant(nom) {
        return new Personne(nom, 0);
    }
}

// Utilisation
const alice = new Personne('Alice', 25);
console.log(alice.sePresenter());
alice.vieillir();
console.log(alice.majeur);  // true

const bebe = Personne.creerEnfant('Bob');</div>

                <h3>Héritage</h3>
                <div class="code-block">class Personne {
    constructor(nom, age) {
        this.nom = nom;
        this.age = age;
    }
    
    sePresenter() {
        return `Je m'appelle ${this.nom}`;
    }
}

class Etudiant extends Personne {
    constructor(nom, age, ecole) {
        super(nom, age);  // Appel du constructeur parent
        this.ecole = ecole;
        this.notes = [];
    }
    
    // Surcharge de méthode
    sePresenter() {
        return `${super.sePresenter()} et j'étudie à ${this.ecole}`;
    }
    
    ajouterNote(note) {
        this.notes.push(note);
    }
    
    calculerMoyenne() {
        if (this.notes.length === 0) return 0;
        const somme = this.notes.reduce((acc, note) => acc + note, 0);
        return somme / this.notes.length;
    }
}

// Utilisation
const etudiant = new Etudiant('Alice', 20, 'Sorbonne');
console.log(etudiant.sePresenter());
etudiant.ajouterNote(15);
etudiant.ajouterNote(17);
console.log(etudiant.calculerMoyenne());  // 16</div>

                <h3>Propriétés Privées (ES2022)</h3>
                <div class="code-block">class CompteBancaire {
    // Propriété privée (commence par #)
    #solde = 0;
    
    constructor(titulaire, soldeInitial = 0) {
        this.titulaire = titulaire;
        this.#solde = soldeInitial;
    }
    
    // Méthode privée
    #verifierSolde(montant) {
        return this.#solde >= montant;
    }
    
    deposer(montant) {
        if (montant > 0) {
            this.#solde += montant;
            return true;
        }
        return false;
    }
    
    retirer(montant) {
        if (this.#verifierSolde(montant)) {
            this.#solde -= montant;
            return true;
        }
        return false;
    }
    
    getSolde() {
        return this.#solde;
    }
}

const compte = new CompteBancaire('Alice', 1000);
compte.deposer(500);
console.log(compte.getSolde());  // 1500
// console.log(compte.#solde);   // Erreur! Propriété privée</div>

                <div class="example">
                    <div class="example-title">📋 Gestionnaire de Livres (POO)</div>
                    <input type="text" id="livre-titre" placeholder="Titre">
                    <input type="text" id="livre-auteur" placeholder="Auteur">
                    <input type="number" id="livre-pages" placeholder="Pages" min="1">
                    <button onclick="ajouterLivre()">Ajouter Livre</button>
                    <div id="livres-result" class="demo-area"></div>
                </div>
            </section>

            <!-- ASYNCHRONE -->
            <section id="async">
                <h2>⏱️ JavaScript Asynchrone</h2>

                <h3>setTimeout et setInterval</h3>
                <div class="code-block">// setTimeout - exécute une fois après un délai
setTimeout(() => {
    console.log('Exécuté après 2 secondes');
}, 2000);

// Avec fonction nommée
function afficherMessage() {
    console.log('Message');
}
const timerId = setTimeout(afficherMessage, 3000);

// Annuler le timeout
clearTimeout(timerId);

// setInterval - exécute répétitivement
let compteur = 0;
const intervalId = setInterval(() => {
    compteur++;
    console.log(`Compteur: ${compteur}`);
    
    if (compteur === 5) {
        clearInterval(intervalId);  // Arrêter après 5 fois
    }
}, 1000);</div>

                <h3>Callbacks</h3>
                <div class="code-block">// Fonction avec callback
function chargerDonnees(callback) {
    setTimeout(() => {
        const donnees = {nom: 'Alice', age: 25};
        callback(donnees);
    }, 1000);
}

// Utilisation
chargerDonnees((resultat) => {
    console.log('Données chargées:', resultat);
});

// Problème: Callback Hell (pyramide de l'enfer)
chargerDonnees1((data1) => {
    chargerDonnees2(data1, (data2) => {
        chargerDonnees3(data2, (data3) => {
            // Code difficile à lire et maintenir
        });
    });
});</div>

                <h3>Promises (ES6)</h3>
                <div class="code-block">// Créer une Promise
function chargerDonnees() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            const succes = true;
            
            if (succes) {
                resolve({nom: 'Alice', age: 25});
            } else {
                reject(new Error('Échec du chargement'));
            }
        }, 1000);
    });
}

// Utiliser une Promise
chargerDonnees()
    .then((donnees) => {
        console.log('Succès:', donnees);
        return donnees.age;
    })
    .then((age) => {
        console.log('Âge:', age);
    })
    .catch((erreur) => {
        console.error('Erreur:', erreur);
    })
    .finally(() => {
        console.log('Terminé');
    });</div>

                <h3>Async/Await (ES2017)</h3>
                <div class="code-block">// Fonction asynchrone
async function chargerEtAfficher() {
    try {
        console.log('Chargement...');
        const donnees = await chargerDonnees();
        console.log('Données:', donnees);
        
        const autreDonnees = await chargerAutresDonnees();
        console.log('Autres:', autreDonnees);
        
        return 'Tout chargé!';
    } catch (erreur) {
        console.error('Erreur:', erreur);
    }
}

// Utilisation
chargerEtAfficher()
    .then(message => console.log(message));

// Ou avec await au niveau supérieur (ES2022)
const resultat = await chargerEtAfficher();</div>

                <h3>Fetch API - Requêtes HTTP</h3>
                <div class="code-block">// GET simple
fetch('https://api.example.com/users')
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Erreur:', error));

// Avec async/await (recommandé)
async function recupererUtilisateurs() {
    try {
        const response = await fetch('https://api.example.com/users');
        
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        
        const data = await response.json();
        return data;
    } catch (error) {
        console.error('Erreur:', error);
    }
}

// POST avec données
async function creerUtilisateur(utilisateur) {
    const response = await fetch('https://api.example.com/users', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
        },
        body: JSON.stringify(utilisateur)
    });
    
    return await response.json();
}

// Utilisation
creerUtilisateur({nom: 'Alice', age: 25});</div>

                <h3>Promise.all et Promise.race</h3>
                <div class="code-block">// Promise.all - Attendre toutes les promises
const promise1 = fetch('url1').then(r => r.json());
const promise2 = fetch('url2').then(r => r.json());
const promise3 = fetch('url3').then(r => r.json());

Promise.all([promise1, promise2, promise3])
    .then(([data1, data2, data3]) => {
        console.log('Toutes les données:', data1, data2, data3);
    })
    .catch(error => {
        console.error('Au moins une a échoué:', error);
    });

// Promise.race - Première promise résolue
Promise.race([promise1, promise2, promise3])
    .then(data => {
        console.log('Première arrivée:', data);
    });

// Promise.allSettled - Toutes, même en cas d'erreur
Promise.allSettled([promise1, promise2, promise3])
    .then(results => {
        results.forEach(result => {
            if (result.status === 'fulfilled') {
                console.log('Succès:', result.value);
            } else {
                console.log('Échec:', result.reason);
            }
        });
    });</div>

                <div class="example">
                    <div class="example-title">📋 Générateur de Citations (API)</div>
                    <button onclick="chargerCitation()">Charger une Citation</button>
                    <button onclick="chargerPlusieursCitations()">Charger 3 Citations</button>
                    <div id="citations-result" class="demo-area"></div>
                </div>

                <div class="example">
                    <div class="example-title">📋 Minuteur Interactif</div>
                    <input type="number" id="timer-seconds" placeholder="Secondes" value="10" min="1" max="60">
                    <button onclick="demarrerMinuteur()">Démarrer</button>
                    <button onclick="arreterMinuteur()">Arrêter</button>
                    <button onclick="resetMinuteur()">Reset</button>
                    <div id="timer-display" style="font-size: 2em; text-align: center; margin: 10px 0;">00:00</div>
                </div>
            </section>

            <!-- BONNES PRATIQUES -->
            <section id="bonnes-pratiques">
                <h2>✨ Bonnes Pratiques et Patterns</h2>

                <h3>Conventions de Nommage</h3>
                <div class="code-block">// Variables et fonctions : camelCase
let monNom = "Alice";
function calculerTotal() {}

// Classes : PascalCase
class MaClasse {}

// Constantes : SCREAMING_SNAKE_CASE
const API_URL = "https://api.example.com";
const MAX_USERS = 100;

// Variables privées : préfixe _
class Exemple {
    _variablePrivee = 42;
}

// Booléens : préfixes is, has, can
let isActive = true;
let hasPermission = false;
let canEdit = true;</div>

                <h3>Destructuration Avancée</h3>
                <div class="code-block">// Paramètres de fonction avec destructuration
function afficherPersonne({nom, age, ville = "Paris"}) {
    console.log(`${nom}, ${age} ans, ${ville}`);
}

afficherPersonne({nom: "Alice", age: 25});

// Swap de variables
let a = 1, b = 2;
[a, b] = [b, a];

// Ignorer des valeurs
const [premier, , troisieme] = [1, 2, 3];

// Destructuration imbriquée
const user = {
    id: 1,
    nom: "Alice",
    adresse: {
        ville: "Paris",
        pays: "France"
    }
};

const {nom, adresse: {ville}} = user;
console.log(ville);  // "Paris"</div>

                <h3>Gestion d'Erreurs</h3>
                <div class="code-block">// Try-Catch
function diviser(a, b) {
    try {
        if (b === 0) {
            throw new Error("Division par zéro impossible");
        }
        return a / b;
    } catch (error) {
        console.error("Erreur:", error.message);
        return null;
    } finally {
        console.log("Opération terminée");
    }
}

// Erreurs personnalisées
class ValidationError extends Error {
    constructor(message) {
        super(message);
        this.name = "ValidationError";
    }
}

function validerAge(age) {
    if (age < 0) {
        throw new ValidationError("L'âge ne peut pas être négatif");
    }
    if (age > 150) {
        throw new ValidationError("L'âge n'est pas réaliste");
    }
    return true;
}

try {
    validerAge(-5);
} catch (error) {
    if (error instanceof ValidationError) {
        console.log("Erreur de validation:", error.message);
    } else {
        throw error;  // Relancer si ce n'est pas une ValidationError
    }
}</div>

                <h3>Optional Chaining (?.) - ES2020</h3>
                <div class="code-block">const user = {
    nom: "Alice",
    adresse: {
        ville: "Paris"
    }
};

// Sans optional chaining (risque d'erreur)
// const code = user.adresse.codePostal.numero;  // TypeError!

// Avec optional chaining
const code = user.adresse?.codePostal?.numero;
console.log(code);  // undefined (pas d'erreur)

// Avec fonctions
const resultat = user.getInfo?.();  // Appelle seulement si existe

// Avec tableaux
const premier = arr?.[0];  // Sécurisé</div>

                <h3>Nullish Coalescing (??) - ES2020</h3>
                <div class="code-block">// Différence entre || et ??

// || retourne la droite si la gauche est "falsy"
const valeur1 = 0 || 10;        // 10
const valeur2 = "" || "texte";  // "texte"

// ?? retourne la droite seulement si la gauche est null ou undefined
const valeur3 = 0 ?? 10;        // 0
const valeur4 = "" ?? "texte";  // ""
const valeur5 = null ?? 10;     // 10
const valeur6 = undefined ?? 10; // 10

// Utile pour valeurs par défaut
function saluer(nom) {
    const nomFinal = nom ?? "Invité";
    return `Bonjour ${nomFinal}`;
}

console.log(saluer());        // "Bonjour Invité"
console.log(saluer("Alice")); // "Bonjour Alice"
console.log(saluer(""));      // "Bonjour " (garde la chaîne vide)</div>

                <h3>Module Pattern</h3>
                <div class="code-block">// Créer un module avec portée privée
const MonModule = (function() {
    // Variables privées
    let compteur = 0;
    
    // Fonctions privées
    function incrementer() {
        compteur++;
    }
    
    // API publique
    return {
        ajouter: function() {
            incrementer();
            console.log(`Compteur: ${compteur}`);
        },
        
        reset: function() {
            compteur = 0;
        },
        
        getCompteur: function() {
            return compteur;
        }
    };
})();

MonModule.ajouter();  // Compteur: 1
MonModule.ajouter();  // Compteur: 2
console.log(MonModule.getCompteur());  // 2
// console.log(MonModule.compteur);  // undefined (privé)</div>

                <h3>Debounce et Throttle</h3>
                <div class="code-block">// Debounce - Retarde l'exécution
function debounce(func, delay) {
    let timeoutId;
    return function(...args) {
        clearTimeout(timeoutId);
        timeoutId = setTimeout(() => func.apply(this, args), delay);
    };
}

// Utilisation : recherche en temps réel
const rechercheInput = document.querySelector('#recherche');
const effectuerRecherche = debounce((terme) => {
    console.log('Recherche:', terme);
    // Appel API...
}, 500);

rechercheInput.addEventListener('input', (e) => {
    effectuerRecherche(e.target.value);
});

// Throttle - Limite la fréquence d'exécution
function throttle(func, limit) {
    let inThrottle;
    return function(...args) {
        if (!inThrottle) {
            func.apply(this, args);
            inThrottle = true;
            setTimeout(() => inThrottle = false, limit);
        }
    };
}

// Utilisation : scroll event
const handleScroll = throttle(() => {
    console.log('Scroll détecté');
}, 1000);

window.addEventListener('scroll', handleScroll);</div>

                <div class="success-box">
                    <strong>✅ Résumé des Bonnes Pratiques :</strong>
                    <ul>
                        <li>Utilisez <code class="code-inline">const</code> par défaut, <code class="code-inline">let</code> si nécessaire</li>
                        <li>Préférez <code class="code-inline">===</code> à <code class="code-inline">==</code></li>
                        <li>Utilisez les fonctions flèches pour les callbacks courts</li>
                        <li>Destructurez les objets et tableaux quand c'est pertinent</li>
                        <li>Gérez toujours les erreurs (try-catch, .catch())</li>
                        <li>Utilisez async/await plutôt que les callbacks</li>
                        <li>Nommez vos variables et fonctions de manière descriptive</li>
                        <li>Commentez le "pourquoi", pas le "quoi"</li>
                        <li>Gardez vos fonctions courtes et focalisées</li>
                        <li>Utilisez les DevTools pour déboguer</li>
                    </ul>
                </div>
            </section>

            <!-- PROJETS PRATIQUES -->
            <section id="projets">
                <h2>🚀 Projets Pratiques Complets</h2>

                <h3>Projet 1 : Todo List Complète</h3>
                <div class="example">
                    <div class="example-title">📋 Application Todo List</div>
                    <div style="max-width: 600px; margin: 0 auto;">
                        <div style="display: flex; gap: 10px; margin-bottom: 15px;">
                            <input type="text" id="todo-input" placeholder="Nouvelle tâche..." style="flex: 1;">
                            <button onclick="ajouterTodo()">Ajouter</button>
                        </div>
                        <div style="display: flex; gap: 10px; margin-bottom: 15px;">
                            <button onclick="filtrerTodos('tous')">Tous</button>
                            <button onclick="filtrerTodos('actifs')">Actifs</button>
                            <button onclick="filtrerTodos('completes')">Complétés</button>
                            <button onclick="viderCompletes()">Vider complétés</button>
                        </div>
                        <ul id="todo-liste" style="list-style: none; padding: 0;"></ul>
                        <div id="todo-stats" style="text-align: center; margin-top: 15px; color: #666;"></div>
                    </div>
                </div>

                <h3>Projet 2 : Calculatrice Avancée</h3>
                <div class="example">
                    <div class="example-title">🔢 Calculatrice Scientifique</div>
                    <div style="max-width: 400px; margin: 0 auto;">
                        <input type="text" id="calc-display" readonly style="width: 100%; font-size: 2em; text-align: right; padding: 10px; margin-bottom: 10px; background: #f0f0f0;">
                        <div style="display: grid; grid-template-columns: repeat(4, 1fr); gap: 5px;">
                            <button onclick="ajouterCalcul('7')">7</button>
                            <button onclick="ajouterCalcul('8')">8</button>
                            <button onclick="ajouterCalcul('9')">9</button>
                            <button onclick="ajouterCalcul('/')" style="background: #ff9800; color: white;">÷</button>
                            <button onclick="ajouterCalcul('4')">4</button>
                            <button onclick="ajouterCalcul('5')">5</button>
                            <button onclick="ajouterCalcul('6')">6</button>
                            <button onclick="ajouterCalcul('*')" style="background: #ff9800; color: white;">×</button>
                            <button onclick="ajouterCalcul('1')">1</button>
                            <button onclick="ajouterCalcul('2')">2</button>
                            <button onclick="ajouterCalcul('3')">3</button>
                            <button onclick="ajouterCalcul('-')" style="background: #ff9800; color: white;">-</button>
                            <button onclick="ajouterCalcul('0')">0</button>
                            <button onclick="ajouterCalcul('.')">.</button>
                            <button onclick="calculerResultat()" style="background: #4caf50; color: white;">=</button>
                            <button onclick="ajouterCalcul('+')" style="background: #ff9800; color: white;">+</button>
                            <button onclick="effacerCalcul()" style="grid-column: 1 / 3; background: #f44336; color: white;">C</button>
                            <button onclick="ajouterCalcul('Math.sqrt(')" style="grid-column: 3 / 5;">√</button>
                        </div>
                    </div>
                </div>
            </section>

            <!-- RESSOURCES -->
            <section id="ressources">
                <h2>📚 Ressources et Références</h2>

                <h3>Documentation Officielle</h3>
                <ul>
                    <li><strong>MDN Web Docs</strong> - Documentation la plus complète et fiable</li>
                    <li><strong>JavaScript.info</strong> - Tutoriels modernes et détaillés</li>
                    <li><strong>ECMAScript Specifications</strong> - Spécifications officielles</li>
                </ul>

                <h3>Outils de Développement</h3>
                <ul>
                    <li><strong>Chrome DevTools</strong> - Déboguer et profiler</li>
                    <li><strong>VS Code</strong> - Éditeur recommandé avec extensions JS</li>
                    <li><strong>Node.js</strong> - Exécuter JS côté serveur</li>
                    <li><strong>npm</strong> - Gestionnaire de paquets</li>
                </ul>

                <h3>Frameworks et Bibliothèques Populaires</h3>
                <div class="grid-2">
                    <div>
                        <h4>Frontend</h4>
                        <ul>
                            <li><strong>React</strong> - Bibliothèque UI (Facebook)</li>
                            <li><strong>Vue.js</strong> - Framework progressif</li>
                            <li><strong>Angular</strong> - Framework complet (Google)</li>
                            <li><strong>Svelte</strong> - Compilateur moderne</li>
                        </ul>
                    </div>
                    <div>
                        <h4>Backend</h4>
                        <ul>
                            <li><strong>Node.js</strong> - Runtime JavaScript</li>
                            <li><strong>Express.js</strong> - Framework web</li>
                            <li><strong>NestJS</strong> - Framework TypeScript</li>
                            <li><strong>Deno</strong> - Runtime moderne</li>
                        </ul>
                    </div>
                </div>

                <h3>Prochaines Étapes</h3>
                <div class="info-box">
                    <strong>Pour continuer votre apprentissage :</strong>
                    <ol>
                        <li><strong>TypeScript</strong> - Ajouter des types statiques à JavaScript</li>
                        <li><strong>Testing</strong> - Jest, Mocha, Cypress pour tester votre code</li>
                        <li><strong>Build Tools</strong> - Webpack, Vite, Parcel pour bundler</li>
                        <li><strong>React/Vue/Angular</strong> - Apprendre un framework moderne</li>
                        <li><strong>Node.js</strong> - Développement backend avec JavaScript</li>
                        <li><strong>APIs REST/GraphQL</strong> - Créer et consommer des APIs</li>
                        <li><strong>Bases de données</strong> - MongoDB, PostgreSQL avec JS</li>
                    </ol>
                </div>
            </section>
        </div>

    </div>
 <script src="protection.js"></script>
    <script>
        // Variables globales pour les exemples
        let compteur = 0;
        let taches = [];
        let contacts = [];
        let livres = [];
        let timerInterval = null;
        let timerSecondes = 0;

        // Exemple: typeof
        function demoTypeof() {
            const result = document.getElementById('demo-typeof');
            result.innerHTML = `
                <strong>Résultats typeof:</strong><br>
                typeof 42 = "${typeof 42}"<br>
                typeof "Hello" = "${typeof "Hello"}"<br>
                typeof true = "${typeof true}"<br>
                typeof {} = "${typeof {}}"<br>
                typeof [] = "${typeof []}"<br>
                typeof null = "${typeof null}"<br>
                typeof undefined = "${typeof undefined}"
            `;
        }

        // Calculatrice simple
        function calculer() {
            const a = parseFloat(document.getElementById('calc-a').value);
            const op = document.getElementById('calc-op').value;
            const b = parseFloat(document.getElementById('calc-b').value);
            let resultat;

            switch(op) {
                case '+': resultat = a + b; break;
                case '-': resultat = a - b; break;
                case '*': resultat = a * b; break;
                case '/': resultat = b !== 0 ? a / b : 'Division par zéro!'; break;
            }

            document.getElementById('calc-result').innerHTML = `
                <strong>Résultat:</strong> ${a} ${op} ${b} = ${resultat}
            `;
        }

        // Vérification d'âge
        function verifierAge() {
            const age = parseInt(document.getElementById('age-input').value);
            let message, couleur;

            if (age < 0) {
                message = "Âge invalide!";
                couleur = "red";
            } else if (age < 13) {
                message = `${age} ans - Vous êtes un enfant`;
                couleur = "blue";
            } else if (age < 18) {
                message = `${age} ans - Vous êtes un adolescent`;
                couleur = "orange";
            } else if (age < 60) {
                message = `${age} ans - Vous êtes un adulte`;
                couleur = "green";
            } else {
                message = `${age} ans - Vous êtes un senior`;
                couleur = "purple";
            }

            const result = document.getElementById('age-result');
            result.innerHTML = `<strong style="color: ${couleur}">${message}</strong>`;
        }

        // Table de multiplication
        function afficherTable() {
            const num = parseInt(document.getElementById('table-num').value);
            let html = `<strong>Table de ${num}:</strong><br>`;

            for (let i = 1; i <= 10; i++) {
                html += `${num} × ${i} = ${num * i}<br>`;
            }

            document.getElementById('table-result').innerHTML = html;
        }

        // Calculateur de moyenne
        function calculerMoyenne() {
            const input = document.getElementById('notes-input').value;
            const notes = input.split(',').map(n => parseFloat(n.trim())).filter(n => !isNaN(n));

            if (notes.length === 0) {
                document.getElementById('moyenne-result').innerHTML = 
                    '<strong style="color: red;">Entrez des notes valides!</strong>';
                return;
            }

            const somme = notes.reduce((acc, note) => acc + note, 0);
            const moyenne = (somme / notes.length).toFixed(2);
            const min = Math.min(...notes);
            const max = Math.max(...notes);

            document.getElementById('moyenne-result').innerHTML = `
                <strong>Statistiques:</strong><br>
                Notes: ${notes.join(', ')}<br>
                Moyenne: <strong>${moyenne}/20</strong><br>
                Min: ${min} | Max: ${max}<br>
                Nombre de notes: ${notes.length}
            `;
        }

        // Gestionnaire de tâches
        function ajouterTache() {
            const input = document.getElementById('tache-input');
            const tache = input.value.trim();

            if (tache) {
                taches.push(tache);
                input.value = '';
                afficherTaches();
            }
        }

        function filtrerTaches() {
            const filtrees = taches.filter(t => t[0] >= 'A' && t[0] <= 'M');
            const result = document.getElementById('taches-result');
            result.innerHTML = '<strong>Tâches (A-M):</strong><br>' +
                (filtrees.length > 0 ? filtrees.join('<br>') : 'Aucune tâche');
        }

        function trierTaches() {
            taches.sort();
            afficherTaches();
        }

        function viderTaches() {
            taches = [];
            afficherTaches();
        }

        function afficherTaches() {
            const result = document.getElementById('taches-result');
            result.innerHTML = '<strong>Tâches:</strong><br>' +
                (taches.length > 0 ? taches.map((t, i) => `${i + 1}. ${t}`).join('<br>') : 'Aucune tâche');
        }

        // Manipulateur DOM
        function changerTexte() {
            const texte = document.getElementById('dom-input').value;
            document.getElementById('demo-dom-text').textContent = texte;
        }

        function toggleClasse() {
            const box = document.getElementById('demo-dom-box');
            box.classList.toggle('highlight');
            if (!document.querySelector('style#demo-style')) {
                const style = document.createElement('style');
                style.id = 'demo-style';
                style.textContent = '.highlight { background: #ffeb3b !important; border: 3px solid #ff9800; }';
                document.head.appendChild(style);
            }
        }

        function changerCouleur() {
            const couleurs = ['#ffcdd2', '#c8e6c9', '#bbdefb', '#f8bbd0', '#d1c4e9'];
            const couleur = couleurs[Math.floor(Math.random() * couleurs.length)];
            document.getElementById('demo-dom-box').style.backgroundColor = couleur;
        }

        function ajouterElement() {
            const p = document.createElement('p');
            p.textContent = `Élément ajouté à ${new Date().toLocaleTimeString()}`;
            p.style.color = '#667eea';
            document.getElementById('demo-dom-box').appendChild(p);
        }

        // Compteur
        function incrementerCompteur() {
            compteur++;
            document.getElementById('compteur-display').textContent = compteur;
        }

        function decrementerCompteur() {
            compteur--;
            document.getElementById('compteur-display').textContent = compteur;
        }

        function resetCompteur() {
            compteur = 0;
            document.getElementById('compteur-display').textContent = compteur;
        }

        function multiplierCompteur() {
            compteur *= 2;
            document.getElementById('compteur-display').textContent = compteur;
        }

        // Liste interactive
        function ajouterItem() {
            const input = document.getElementById('item-input');
            const texte = input.value.trim();

            if (texte) {
                const li = document.createElement('li');
                li.innerHTML = `
                    <span style="flex: 1;">${texte}</span>
                    <button style="background: #f44336; font-size: 0.8em; padding: 5px 10px;">Supprimer</button>
                `;
                li.style.cssText = 'display: flex; align-items: center; gap: 10px; padding: 10px; background: #f8f9fa; margin: 5px 0; border-radius: 5px;';

                document.getElementById('liste-interactive').appendChild(li);
                input.value = '';
            }
        }

        // Délégation d'événements pour la liste
        document.addEventListener('DOMContentLoaded', () => {
            const liste = document.getElementById('liste-interactive');
            if (liste) {
                liste.addEventListener('click', (e) => {
                    if (e.target.tagName === 'BUTTON') {
                        e.target.parentElement.remove();
                    } else if (e.target.tagName === 'SPAN') {
                        e.target.parentElement.style.opacity = 
                            e.target.parentElement.style.opacity === '0.5' ? '1' : '0.5';
                    }
                });
            }
        });

        // Contacts
        function ajouterContact() {
            const nom = document.getElementById('contact-nom').value.trim();
            const email = document.getElementById('contact-email').value.trim();
            const tel = document.getElementById('contact-tel').value.trim();

            if (nom && email) {
                contacts.push({nom, email, tel});
                document.getElementById('contact-nom').value = '';
                document.getElementById('contact-email').value = '';
                document.getElementById('contact-tel').value = '';
                afficherContacts();
            }
        }

        function afficherContacts() {
            const result = document.getElementById('contacts-result');
            if (contacts.length === 0) {
                result.innerHTML = 'Aucun contact';
                return;
            }

            result.innerHTML = '<strong>Contacts:</strong><br>' +
                contacts.map((c, i) => `
                    ${i + 1}. <strong>${c.nom}</strong><br>
                    📧 ${c.email}<br>
                    📞 ${c.tel || 'N/A'}<br>
                `).join('<br>');
        }

        // Livres POO
        class Livre {
            constructor(titre, auteur, pages) {
                this.titre = titre;
                this.auteur = auteur;
                this.pages = pages;
            }

            decrire() {
                return `"${this.titre}" par ${this.auteur} (${this.pages} pages)`;
            }
        }

        function ajouterLivre() {
            const titre = document.getElementById('livre-titre').value.trim();
            const auteur = document.getElementById('livre-auteur').value.trim();
            const pages = parseInt(document.getElementById('livre-pages').value);

            if (titre && auteur && pages > 0) {
                const livre = new Livre(titre, auteur, pages);
                livres.push(livre);
                document.getElementById('livre-titre').value = '';
                document.getElementById('livre-auteur').value = '';
                document.getElementById('livre-pages').value = '';
                afficherLivres();
            }
        }

        function afficherLivres() {
            const result = document.getElementById('livres-result');
            if (livres.length === 0) {
                result.innerHTML = 'Aucun livre';
                return;
            }

            const totalPages = livres.reduce((acc, l) => acc + l.pages, 0);
            result.innerHTML = '<strong>Bibliothèque:</strong><br>' +
                livres.map((l, i) => `${i + 1}. ${l.decrire()}`).join('<br>') +
                `<br><br><strong>Total: ${livres.length} livres (${totalPages} pages)</strong>`;
        }

        // Citations API
        async function chargerCitation() {
            const result = document.getElementById('citations-result');
            result.innerHTML = '<em>Chargement...</em>';
            
            try {
                const response = await fetch('https://api.quotable.io/random');
                const data = await response.json();
                result.innerHTML = `
                    <blockquote style="border-left: 4px solid #667eea; padding-left: 15px; font-style: italic;">
                        "${data.content}"
                        <footer style="margin-top: 10px; font-style: normal; color: #666;">
                            — ${data.author}
                        </footer>
                    </blockquote>
                `;
            } catch (error) {
                result.innerHTML = '<strong style="color: red;">Erreur de chargement</strong>';
            }
        }

        async function chargerPlusieursCitations() {
            const result = document.getElementById('citations-result');
            result.innerHTML = '<em>Chargement de 3 citations...</em>';
            
            try {
                const promises = [
                    fetch('https://api.quotable.io/random').then(r => r.json()),
                    fetch('https://api.quotable.io/random').then(r => r.json()),
                    fetch('https://api.quotable.io/random').then(r => r.json())
                ];
                
                const citations = await Promise.all(promises);
                
                result.innerHTML = citations.map((data, i) => `
                    <div style="margin: 10px 0; padding: 10px; background: #f8f9fa; border-radius: 5px;">
                        <strong>${i + 1}.</strong> "${data.content}"
                        <div style="text-align: right; color: #666; margin-top: 5px;">— ${data.author}</div>
                    </div>
                `).join('');
            } catch (error) {
                result.innerHTML = '<strong style="color: red;">Erreur de chargement</strong>';
            }
        }

        // Minuteur
        function demarrerMinuteur() {
            if (timerInterval) return;
            
            timerSecondes = parseInt(document.getElementById('timer-seconds').value) || 10;
            
            timerInterval = setInterval(() => {
                timerSecondes--;
                afficherMinuteur();
                
                if (timerSecondes <= 0) {
                    arreterMinuteur();
                    alert('⏰ Temps écoulé!');
                }
            }, 1000);
        }

        function arreterMinuteur() {
            if (timerInterval) {
                clearInterval(timerInterval);
                timerInterval = null;
            }
        }

        function resetMinuteur() {
            arreterMinuteur();
            timerSecondes = parseInt(document.getElementById('timer-seconds').value) || 10;
            afficherMinuteur();
        }

        function afficherMinuteur() {
            const minutes = Math.floor(timerSecondes / 60);
            const secondes = timerSecondes % 60;
            document.getElementById('timer-display').textContent = 
                `${String(minutes).padStart(2, '0')}:${String(secondes).padStart(2, '0')}`;
        }

        // Todo List complète
        class Todo {
            constructor(texte) {
                this.id = Date.now();
                this.texte = texte;
                this.complete = false;
            }
        }

        let filtreActuel = 'tous';

        function ajouterTodo() {
            const input = document.getElementById('todo-input');
            const texte = input.value.trim();

            if (texte) {
                todos.push(new Todo(texte));
                input.value = '';
                afficherTodos();
            }
        }

        function toggleTodo(id) {
            const todo = todos.find(t => t.id === id);
            if (todo) {
                todo.complete = !todo.complete;
                afficherTodos();
            }
        }

        function supprimerTodo(id) {
            todos = todos.filter(t => t.id !== id);
            afficherTodos();
        }

        function filtrerTodos(filtre) {
            filtreActuel = filtre;
            afficherTodos();
        }

        function viderCompletes() {
            todos = todos.filter(t => !t.complete);
            afficherTodos();
        }

        function afficherTodos() {
            const liste = document.getElementById('todo-liste');
            const stats = document.getElementById('todo-stats');

            let todosAffiches = todos;
            if (filtreActuel === 'actifs') {
                todosAffiches = todos.filter(t => !t.complete);
            } else if (filtreActuel === 'completes') {
                todosAffiches = todos.filter(t => t.complete);
            }

            if (todosAffiches.length === 0) {
                liste.innerHTML = '<li style="text-align: center; color: #999;">Aucune tâche</li>';
            } else {
                liste.innerHTML = todosAffiches.map(todo => `
                    <li style="display: flex; align-items: center; gap: 10px; padding: 12px; background: ${todo.complete ? '#f0f0f0' : 'white'}; margin: 5px 0; border-radius: 5px; border: 1px solid #ddd;">
                        <input type="checkbox" ${todo.complete ? 'checked' : ''} 
                               onchange="toggleTodo(${todo.id})" 
                               style="width: 20px; height: 20px; cursor: pointer;">
                        <span style="flex: 1; ${todo.complete ? 'text-decoration: line-through; color: #999;' : ''}">${todo.texte}</span>
                        <button onclick="supprimerTodo(${todo.id})" 
                                style="background: #f44336; font-size: 0.8em; padding: 5px 10px;">
                            ✕
                        </button>
                    </li>
                `).join('');
            }

            const actifs = todos.filter(t => !t.complete).length;
            const completes = todos.filter(t => t.complete).length;
            stats.innerHTML = `${actifs} actives • ${completes} complétées • ${todos.length} total`;
        }

        // Calculatrice avancée
        function ajouterCalcul(valeur) {
            const display = document.getElementById('calc-display');
            calcDisplay += valeur;
            display.value = calcDisplay;
        }

        function calculerResultat() {
            const display = document.getElementById('calc-display');
            try {
                calcDisplay = eval(calcDisplay).toString();
                display.value = calcDisplay;
            } catch (error) {
                display.value = 'Erreur';
                calcDisplay = '';
            }
        }

        function effacerCalcul() {
            calcDisplay = '';
            document.getElementById('calc-display').value = '';
        }

        // Initialisation
        document.addEventListener('DOMContentLoaded', () => {
            afficherMinuteur();
        });
    </script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            padding: 20px;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            background: white;
            border-radius: 15px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            overflow: hidden;
        }

        header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 40px;
            text-align: center;
        }

        header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
        }

        .badge {
            display: inline-block;
            background: rgba(255,255,255,0.2);
            padding: 5px 15px;
            border-radius: 20px;
            margin: 5px;
            font-size: 0.9em;
        }

        .nav {
            background: #2d3748;
            padding: 15px;
            position: sticky;
            top: 0;
            z-index: 100;
            overflow-x: auto;
        }

        .nav ul {
            list-style: none;
            display: flex;
            gap: 10px;
            justify-content: center;
            flex-wrap: wrap;
        }

        .nav a {
            color: white;
            text-decoration: none;
            padding: 8px 16px;
            border-radius: 5px;
            transition: all 0.3s;
            white-space: nowrap;
        }

        .nav a:hover {
            background: #667eea;
            transform: translateY(-2px);
        }

        .content {
            padding: 40px;
        }

        section {
            margin-bottom: 60px;
            scroll-margin-top: 80px;
        }

        h2 {
            color: #667eea;
            font-size: 2em;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 3px solid #667eea;
        }

        h3 {
            color: #764ba2;
            font-size: 1.5em;
            margin: 30px 0 15px;
        }

        h4 {
            color: #2d3748;
            font-size: 1.2em;
            margin: 20px 0 10px;
        }

        /* ÉDITEUR DE CODE INTERACTIF */
        .code-editor {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin: 20px 0;
            border: 2px solid #667eea;
            border-radius: 10px;
            overflow: hidden;
            background: #1e1e1e;
        }

        .editor-panel {
            display: flex;
            flex-direction: column;
        }

        .editor-header {
            background: #2d3748;
            color: white;
            padding: 10px 15px;
            font-weight: bold;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .editor-content {
            flex: 1;
            position: relative;
        }

        .code-input {
            width: 100%;
            height: 300px;
            padding: 15px;
            background: #1e1e1e;
            color: #e0e0e0;
            border: none;
            font-family: 'Courier New', monospace;
            font-size: 14px;
            resize: vertical;
            outline: none;
        }

        .output-area {
            background: white;
            color: #333;
            padding: 15px;
            height: 300px;
            overflow-y: auto;
            font-family: 'Courier New', monospace;
            font-size: 14px;
        }

        .run-button {
            background: #4caf50;
            color: white;
            border: none;
            padding: 8px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 0.9em;
            transition: all 0.3s;
        }

        .run-button:hover {
            background: #45a049;
            transform: scale(1.05);
        }

        .reset-button {
            background: #ff9800;
            color: white;
            border: none;
            padding: 8px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 0.9em;
            margin-left: 5px;
        }

        /* CODE STATIQUE */
        .code-block {
            background: #2d3748;
            color: #e2e8f0;
            padding: 20px;
            border-radius: 8px;
            margin: 20px 0;
            overflow-x: auto;
            font-family: 'Courier New', monospace;
            position: relative;
            font-size: 14px;
            line-height: 1.5;
        }

        .code-block::before {
            content: 'JavaScript';
            position: absolute;
            top: 5px;
            right: 10px;
            background: #667eea;
            color: white;
            padding: 2px 10px;
            border-radius: 3px;
            font-size: 0.8em;
        }

        .copy-button {
            position: absolute;
            top: 40px;
            right: 10px;
            background: #667eea;
            color: white;
            border: none;
            padding: 5px 10px;
            border-radius: 3px;
            cursor: pointer;
            font-size: 0.8em;
            opacity: 0.7;
            transition: opacity 0.3s;
        }

        .copy-button:hover {
            opacity: 1;
        }

        .info-box {
            background: #e3f2fd;
            border-left: 4px solid #2196f3;
            padding: 20px;
            margin: 20px 0;
            border-radius: 5px;
        }

        .warning-box {
            background: #fff3cd;
            border-left: 4px solid #ffc107;
            padding: 20px;
            margin: 20px 0;
            border-radius: 5px;
        }

        .success-box {
            background: #d4edda;
            border-left: 4px solid #28a745;
            padding: 20px;
            margin: 20px 0;
            border-radius: 5px;
        }

        .example {
            background: #f8f9fa;
            border: 2px solid #dee2e6;
            border-radius: 8px;
            padding: 20px;
            margin: 20px 0;
        }

        .example-title {
            font-weight: bold;
            color: #667eea;
            margin-bottom: 15px;
            font-size: 1.1em;
        }

        button:not(.run-button):not(.reset-button):not(.copy-button) {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1em;
            transition: transform 0.2s, box-shadow 0.2s;
            margin: 5px;
        }

        button:hover:not(.run-button):not(.reset-button) {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }

        .console-output {
            background: #1e1e1e;
            color: #4caf50;
            padding: 15px;
            border-radius: 5px;
            margin: 10px 0;
            font-family: 'Courier New', monospace;
            min-height: 100px;
            max-height: 300px;
            overflow-y: auto;
        }

        .console-line {
            margin: 5px 0;
            padding: 5px;
            border-left: 3px solid #4caf50;
            padding-left: 10px;
        }

        .console-error {
            color: #f44336;
            border-left-color: #f44336;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
        }

        table th {
            background: #667eea;
            color: white;
            padding: 12px;
            text-align: left;
        }

        table td {
            padding: 12px;
            border-bottom: 1px solid #dee2e6;
        }

        ul, ol {
            margin: 15px 0 15px 30px;
        }

        li {
            margin-bottom: 8px;
        }

        .tabs {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
            border-bottom: 2px solid #dee2e6;
        }

        .tab {
            padding: 10px 20px;
            background: transparent;
            border: none;
            cursor: pointer;
            color: #666;
            transition: all 0.3s;
        }

        .tab.active {
            color: #667eea;
            border-bottom: 3px solid #667eea;
            margin-bottom: -2px;
        }

        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
        }

        footer {
            background: #2d3748;
            color: white;
            padding: 30px;
            text-align: center;
        }

        @media (max-width: 768px) {
            .code-editor {
                grid-template-columns: 1fr;
            }
            
            header h1 {
                font-size: 1.8em;
            }
            
            .content {
                padding: 20px;
            }
        }

        /* Animation pour les résultats */
        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .animated {
            animation: fadeIn 0.3s ease-in;
        }
    </style>
</head>

 <script src="protection.js"></script>
    <script>
        // Exemples de code par défaut
        const codeExemples = {
            variables: `// Testez les variables !
const prenom = "Alice";
const age = 25;

console.log(\`Je m'appelle \${prenom}\`);
console.log(\`J'ai \${age} ans\`);

// Modifiez et ajoutez votre code ici
const ville = "Paris";
console.log(\`J'habite à \${ville}\`);`
        };

        // Fonction pour exécuter le code JavaScript
        function executerCode(editorId, outputId) {
            const editor = document.getElementById(editorId);
            const output = document.getElementById(outputId);
            const code = editor.value;

            // Capturer console.log
            let logs = [];
            const originalLog = console.log;
            console.log = function(...args) {
                logs.push(args.map(arg => {
                    if (typeof arg === 'object') {
                        return JSON.stringify(arg, null, 2);
                    }
                    return String(arg);
                }).join(' '));
                originalLog.apply(console, args);
            };

            try {
                // Exécuter le code
                eval(code);
                
                // Afficher les résultats
                if (logs.length > 0) {
                    output.innerHTML = logs.map(log => 
                        `<div class="console-line">${log}</div>`
                    ).join('');
                } else {
                    output.innerHTML = '<div class="console-line">Code exécuté avec succès (pas de sortie console)</div>';
                }
                
                output.classList.add('animated');
            } catch (error) {
                output.innerHTML = `<div class="console-line console-error">❌ Erreur: ${error.message}</div>`;
            } finally {
                // Restaurer console.log
                console.log = originalLog;
                
                // Retirer l'animation après
                setTimeout(() => output.classList.remove('animated'), 300);
            }
        }

        // Fonction pour exécuter du code asynchrone
        async function executerCodeAsync(editorId, outputId) {
            const editor = document.getElementById(editorId);
            const output = document.getElementById(outputId);
            const code = editor.value;

            let logs = [];
            const originalLog = console.log;
            console.log = function(...args) {
                logs.push(args.map(arg => {
                    if (typeof arg === 'object') {
                        return JSON.stringify(arg, null, 2);
                    }
                    return String(arg);
                }).join(' '));
                originalLog.apply(console, args);
            };

            try {
                // Créer une fonction async et l'exécuter
                const asyncFunc = new Function(`
                    return (async () => {
                        ${code}
                    })();
                `);
                
                await asyncFunc();
                
                if (logs.length > 0) {
                    output.innerHTML = logs.map(log => 
                        `<div class="console-line">${log}</div>`
                    ).join('');
                } else {
                    output.innerHTML = '<div class="console-line">Code exécuté (pas de sortie)</div>';
                }
            } catch (error) {
                output.innerHTML = `<div class="console-line console-error">❌ Erreur: ${error.message}</div>`;
            } finally {
                console.log = originalLog;
            }
        }

        // Reset le code
        function resetCode(editorId, defaultCode) {
            document.getElementById(editorId).value = defaultCode;
        }

        // Copier le code
        function copierCode(button) {
            const codeBlock = button.parentElement;
            const code = codeBlock.textContent.replace('📋 Copier', '').replace('JavaScript', '').trim();
            
            navigator.clipboard.writeText(code).then(() => {
                const originalText = button.textContent;
                button.textContent = '✅ Copié!';
                setTimeout(() => {
                    button.textContent = originalText;
                }, 2000);
            });
        }

        // Gestion des tabs
        let currentTab = 0;
        function changerTab(index) {
            const tabs = document.querySelectorAll('.tab');
            const contents = document.querySelectorAll('.tab-content');
            
            tabs.forEach((tab, i) => {
                if (i === index) {
                    tab.classList.add('active');
                    contents[i].classList.add('active');
                } else {
                    tab.classList.remove('active');
                    contents[i].classList.remove('active');
                }
            });
            
            currentTab = index;
        }

        // Manipulation DOM
        function changerTexteDom() {
            const texte = document.getElementById('demo-input').value;
            document.getElementById('demo-text').textContent = texte;
        }

        function changerCouleurDom() {
            const couleurs = ['#ffcdd2', '#c8e6c9', '#bbdefb', '#f8bbd0', '#d1c4e9', '#ffe0b2'];
            const couleur = couleurs[Math.floor(Math.random() * couleurs.length)];
            document.getElementById('demo-box').style.backgroundColor = couleur;
        }

        function ajouterElementDom() {
            const p = document.createElement('p');
            p.textContent = `Ajouté à ${new Date().toLocaleTimeString()}`;
            p.style.color = '#667eea';
            p.style.animation = 'fadeIn 0.3s';
            document.getElementById('demo-box').appendChild(p);
        }

        // Test API
        async function testerAPI() {
            const result = document.getElementById('api-result');
            result.innerHTML = '<div style="text-align: center;">⏳ Chargement...</div>';
            
            try {
                const response = await fetch('https://api.quotable.io/random');
                const data = await response.json();
                
                result.innerHTML = `
                    <blockquote style="border-left: 4px solid #667eea; padding-left: 15px; font-style: italic; margin: 0;">
                        <p style="font-size: 1.1em; margin-bottom: 10px;">"${data.content}"</p>
                        <footer style="text-align: right; color: #666;">— ${data.author}</footer>
                    </blockquote>
                `;
            } catch (error) {
                result.innerHTML = '<div style="color: red;">❌ Erreur de chargement</div>';
            }
        }

        // Todo List
        let todos = [];
        let todoId = 0;

        function ajouterTodo() {
            const input = document.getElementById('todo-input');
            const texte = input.value.trim();
            
            if (texte) {
                todos.push({
                    id: todoId++,
                    texte: texte,
                    complete: false
                });
                input.value = '';
                afficherTodos();
            }
        }

        function toggleTodo(id) {
            const todo = todos.find(t => t.id === id);
            if (todo) {
                todo.complete = !todo.complete;
                afficherTodos();
            }
        }

        function supprimerTodo(id) {
            todos = todos.filter(t => t.id !== id);
            afficherTodos();
        }

        function afficherTodos() {
            const liste = document.getElementById('todo-list');
            const stats = document.getElementById('todo-stats');
            
            if (todos.length === 0) {
                liste.innerHTML = '<li style="text-align: center; color: #999; padding: 20px;">Aucune tâche</li>';
                stats.innerHTML = '';
                return;
            }
            
            liste.innerHTML = todos.map(todo => `
                <li style="display: flex; align-items: center; gap: 10px; padding: 12px; background: ${todo.complete ? '#f0f0f0' : 'white'}; margin: 8px 0; border-radius: 5px; border: 1px solid #ddd; transition: all 0.3s;">
                    <input type="checkbox" ${todo.complete ? 'checked' : ''} 
                           onchange="toggleTodo(${todo.id})" 
                           style="width: 18px; height: 18px; cursor: pointer;">
                    <span style="flex: 1; ${todo.complete ? 'text-decoration: line-through; color: #999;' : ''}">${todo.texte}</span>
                    <button onclick="supprimerTodo(${todo.id})" 
                            style="background: #f44336; padding: 5px 10px; font-size: 0.9em; border-radius: 3px;">
                        🗑️
                    </button>
                </li>
            `).join('');
            
            const actifs = todos.filter(t => !t.complete).length;
            const completes = todos.filter(t => t.complete).length;
            stats.innerHTML = `${actifs} active${actifs > 1 ? 's' : ''} • ${completes} terminée${completes > 1 ? 's' : ''}`;
        }

        // Calculatrice
        let calcDisplay = '';

        function ajouterCalc(valeur) {
            calcDisplay += valeur;
            document.getElementById('calc-display').value = calcDisplay;
        }

        function calculer() {
            try {
                calcDisplay = eval(calcDisplay.replace('×', '*').replace('÷', '/').replace('−', '-')).toString();
                document.getElementById('calc-display').value = calcDisplay;
            } catch {
                document.getElementById('calc-display').value = 'Erreur';
                calcDisplay = '';
            }
        }

        function effacerCalc() {
            calcDisplay = '';
            document.getElementById('calc-display').value = '';
        }

        // Générateur de couleurs
        function genererCouleur() {
            const r = Math.floor(Math.random() * 256);
            const g = Math.floor(Math.random() * 256);
            const b = Math.floor(Math.random() * 256);
            const hex = '#' + [r, g, b].map(x => x.toString(16).padStart(2, '0')).join('');
            
            document.getElementById('color-display').style.backgroundColor = hex;
            document.getElementById('color-code').textContent = hex;
        }

        function copierCouleur() {
            const code = document.getElementById('color-code').textContent;
            navigator.clipboard.writeText(code).then(() => {
                const btn = event.target;
                const originalText = btn.textContent;
                btn.textContent = '✅ Copié!';
                setTimeout(() => {
                    btn.textContent = originalText;
                }, 2000);
            });
        }

        // Initialisation
        document.addEventListener('DOMContentLoaded', () => {
            console.log('Formation JavaScript Interactive chargée!');
        });
    </script>
    
</body>
