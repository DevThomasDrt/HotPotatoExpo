# Guide de Configuration pour Google Play Store

## 🚀 Étapes de Préparation pour la Publication

### 1. Configuration AdMob (OBLIGATOIRE)

#### A. Créer un compte AdMob
1. Aller sur https://admob.google.com/
2. Créer un compte avec le même email que Google Play Console
3. Créer une nouvelle application "Hot Potato"

#### B. Obtenir les IDs AdMob
1. **App ID Android** : Remplacer dans `app.json`
   ```json
   "android_app_id": "VOTRE_VRAI_APP_ID_ANDROID"
   ```

2. **Unit ID Interstitial** : Remplacer dans `src/services/AdService.js` ligne 16
   ```javascript
   interstitial: __DEV__ ? TestIds.INTERSTITIAL : 'VOTRE_VRAI_INTERSTITIAL_ID'
   ```

### 2. Configuration des Achats In-App (OBLIGATOIRE)

#### A. Dans Google Play Console
1. Aller dans "Monétisation" > "Produits in-app"
2. Créer un produit avec l'ID : `premium_upgrade`
3. Prix recommandé : 2,99€
4. Titre : "Version Premium"
5. Description : "Débloquez toutes les fonctionnalités premium"

#### B. Tester les achats
1. Ajouter des comptes de test dans Play Console
2. Utiliser ces comptes pour tester les achats

### 3. Assets Requis pour le Play Store

#### A. Icônes et Screenshots
- ✅ Icône de l'app (512x512) : `assets/logo.png`
- ❌ Screenshots (au moins 2) : À créer
- ❌ Feature Graphic (1024x500) : À créer

#### B. Descriptions
- ❌ Titre court (30 caractères max)
- ❌ Description courte (80 caractères max)
- ❌ Description complète (4000 caractères max)

### 4. Politique de Confidentialité (OBLIGATOIRE)

#### Contenu requis :
- Collecte de données (AdMob, achats)
- Utilisation des données
- Partage avec des tiers
- Droits des utilisateurs

### 5. Permissions Android

✅ Déjà configurées dans `app.json` :
- `INTERNET` : Pour les publicités
- `ACCESS_NETWORK_STATE` : Pour vérifier la connexion
- `VIBRATE` : Pour les vibrations du jeu

### 6. Compilation de Production

#### Commandes à exécuter :
```bash
# 1. Se connecter à Expo
eas login

# 2. Compiler l'AAB pour le Play Store
eas build --platform android --profile production

# 3. Télécharger l'AAB généré
# Le fichier sera disponible sur expo.dev
```

### 7. Checklist Finale

- [ ] IDs AdMob remplacés par les vrais
- [ ] Produit IAP créé dans Play Console
- [ ] Screenshots créés (minimum 2)
- [ ] Feature Graphic créé
- [ ] Descriptions rédigées
- [ ] Politique de confidentialité publiée
- [ ] AAB compilé et testé
- [ ] Compte développeur Google Play (25$ one-time)

### 8. Publication

1. **Upload de l'AAB** dans Play Console
2. **Remplir les métadonnées** (descriptions, screenshots)
3. **Configurer la tarification** (gratuit avec achats in-app)
4. **Soumettre pour révision** (peut prendre 1-3 jours)

---

## ⚠️ IMPORTANT

**Avant la compilation finale :**
1. Remplacer TOUS les IDs de test par les vrais IDs
2. Tester l'application avec les vrais IDs AdMob
3. Vérifier que les achats in-app fonctionnent
4. S'assurer que l'application fonctionne sans erreurs

**Coûts :**
- Compte Google Play Developer : 25$ (une fois)
- Compte AdMob : Gratuit
- Compilation EAS : Gratuit (plan hobby)