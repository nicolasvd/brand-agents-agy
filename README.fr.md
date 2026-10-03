<p align="center">
  <img src="banner.svg" alt="AI Brand Strategy Team - Antigravity Native" width="100%" />
</p>

# AI Brand Strategy Team — Antigravity Native

[![Release](https://img.shields.io/badge/Release-v1.0.0-blue.svg?style=flat-square)](https://github.com/nicolasvd/brand-agents-agy/releases)
[![Runtime](https://img.shields.io/badge/Runtime-Google%20Antigravity%202.0-4285F4.svg?style=flat-square)](https://antigravity.google)
[![Architecture](https://img.shields.io/badge/Architecture-Hub%20%26%20Spoke%20Declarative-success.svg?style=flat-square)](#-architecture-des-dossiers-hub--spoke)
[![Engine](https://img.shields.io/badge/Engine-Multi--Model%20AI-8E75C4.svg?style=flat-square)](#)
[![Dependencies](https://img.shields.io/badge/Dependencies-Z%C3%A9ro%20(Sans%20Python%2FNode)-brightgreen.svg?style=flat-square)](#)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg?style=flat-square)](LICENSE)

> [🇬🇧 English](README.md) | 🇫🇷 **Français**

Framework autonome d'audit stratégique de marque et d'intelligence réseaux sociaux omnicanale, conçu nativement pour **Google Antigravity (Standalone / v2.0)** et orchestré par **l'IA Multi-Modèles (Gemini, Claude, OpenAI)**. À partir d'une simple URL de marque, il cartographie l'empreinte digitale, pilote des sessions de navigation réelles pour auditer les canaux sociaux sans blocage, échantillonne les verbatims authentiques, analyse les aperçus Dark Social et génère des livrables visuels de niveau exécutif adossés à des archives Markdown permanentes.

---

## 🚀 Démarrage Rapide

### Lancement en 1 Minute (Zéro Dépendance)

Aucun gestionnaire de paquets (`npm`, `pip`), environnement virtuel ou clé d'API externe n'est requis.

1. **Cloner ou Télécharger le Répertoire :**
   ```bash
   git clone https://github.com/nicolasvd/brand-agents-agy.git mon-audit-marque
   cd mon-audit-marque
   ```
2. **Ouvrir dans Google Antigravity :**
   Lancez Antigravity, cliquez sur **Open Folder**, puis sélectionnez `mon-audit-marque`.
3. **Lancer un Audit :**
   Dans le chat d'Antigravity, écrivez simplement :
   ```text
   Audit https://example.com
   ```
   *L'orchestrateur `brand-lead` explore la page d'accueil, cartographie les canaux sociaux, déploie les scanners en parallèle et synthétise l'audit stratégique.*
4. **Consulter les Livrables dans le Cockpit :**
   Ouvrez `reports/index.html` dans votre navigateur. Dès qu'un audit est finalisé, appuyez sur **Cmd + R** (ou **F5**) pour actualiser le portail et consulter vos rapports.

---

## 🏛️ Architecture Multi-Agents (Vagues 1, 2 et 3)

```mermaid
flowchart TD
    subgraph Wave1["Vague 1 : Empreinte Digitale & Scanners Omnicanaux"]
        A["URL de la Marque"] --> B["brand-sub-hub-crawler"]
        B --> C["Proposition de Valeur, Dark Social, Liens Sociaux & Stores Mobiles"]
        C --> D["Scanners Navigateur Réel (Parallèle)"]
        D --> D1["Scanner LinkedIn"]
        D --> D2["Scanner Instagram"]
        D --> D3["Scanner TikTok"]
        D --> D4["Scanner Facebook"]
        D --> D5["Scanner YouTube"]
        D --> D6["Scanner X (Twitter)"]
        D --> D7["Scanner iOS App Store"]
        D --> D8["Scanner Android Play Store"]
    end

    subgraph Wave2["Vague 2 : Synthèse Stratégique & Intelligence Longitudinale"]
        D1 & D2 & D3 & D4 & D5 & D6 & D7 & D8 --> E["brand-sub-analyst"]
        E --> F["Ratio Conversationnel & Confrontation Sémantique"]
        E --> G["Vélocité Longitudinale & Trajectoires d'Engagement (Δ)"]
        E --> H["Matrice de Résolution des Failles & Blueprint en 4 Niveaux"]
        E --> I["Brouillons : w2-draft-audit.md + w2-draft-brandbook.md"]
    end

    subgraph Wave3["Vague 3 : Promotion des Livrables & Compilation HTML Asynchrone"]
        I --> J["Promotion vers reports/{slug}/markdown/"]
        J --> K["brand-sub-styler (Compilateur Asynchrone)"]
        K --> L["OVERVIEW.html (Hub Exécutif)"]
        K --> M["STRATEGIC-AUDIT.html (Critique & Scorecard)"]
        K --> N["channels/*.html (Rapports Sociaux & Stores Dédiés)"]
        K --> O["reports/index.html (Mise à jour du Cockpit)"]
        K --> P["Sentinelle .done & Nettoyage GC du Scratchpad"]
    end
```

### Vague 1 : Exploration Factualisée (Zero-Knowledge)
- **`brand-sub-hub-crawler`** : Visite la page d'accueil avec hydratation SPA complète (React, Vue, Next.js). Capture la preuve visuelle au-dessus de la ligne de flottaison, extrait les métadonnées Open Graph (`og:*`, `twitter:*`), analyse le `<head>` pour les Smart App Banners iOS (`<meta name="apple-itunes-app">`), et cartographie l'ensemble des liens sociaux et magasins d'applications.
- **Scanners Navigateur Natifs** : Pilotent des sessions Chrome réelles pour contourner les protections anti-scraping sur LinkedIn, Instagram, TikTok, Facebook, YouTube, X, Apple App Store et Google Play Store.
  - Les scanners sociaux extraient les métriques communautaires réelles (zéro vanity metric de following) et échantillonnent 3 à 5 verbatims authentiques (`comment-sampling`).
  - Les scanners d'applications mobiles auditent la note moyenne (/5.0), le volume d'avis, le palier public de téléchargements (`1M+`, `500k+`), l'historique de versions et les avis récents avec réponses officielles de l'éditeur.
  - Sentinelle Fast-Exit (`NONE_OR_DISABLED`, `NONE_OR_EMPTY`) en l'absence de commentaires ou d'avis.

### Vague 2 : Diagnostic Stratégique & Longitudinal
- **`brand-sub-analyst`** : Ingeste les données de la Vague 1 et les archives historiques.
  - Évalue la cohérence de la Tonalité (ToV) et calcule le Ratio Conversationnel ($\frac{\text{Commentaires}}{\text{Réactions}}$).
  - Applique le plafonnement strict à 6.5/10 de la Tonalité si des frictions SAV restent sans réponse, si la note mobile moyenne est $< 3.0 / 5.0$, ou si le taux de réponse développeur aux avis critiques 1-2★ est $< 20\%$.
  - Attribue un bonus commercial (+0.5 pt) pour les applications mobiles performantes ($\ge 4.4 / 5.0$ et $\ge 1\text{M}+$ téléchargements).
  - Suit l'évolution des failles entre audits (`🟢 RESOLVED`, `🟡 IN_PROGRESS`, `🔴 PERSISTENT`).
  - Rédige un plan d'action standardisé en 4 niveaux pour chaque faille non résolue.

### Vague 3 : Promotion & Compilation HTML Découplée
- **`brand-sub-styler`** : Compilateur HTML hors-ligne, déterministe. Lit directement depuis les archives permanentes `reports/{slug}/markdown/` et compile des interfaces soignées avec design tokens partagés et liens bidirectionnels vers les sources Markdown. Génère des spokes dédiés pour les réseaux sociaux et les magasins d'applications (`channels/appstore.html`, `channels/playstore.html`), avec encarts de versions et badges de réponses développeur. Bootstrappe automatiquement `reports/index.html` lors du premier audit.

---

## 🔄 Protocole de Ré-Audit Incrémental

Lors du ré-audit d'une marque déjà analysée :
1. **Détection d'Archive :** `brand-lead` détecte la présence de `reports/{slug}/markdown/REVERSE-BRAND-BOOK.md` et active automatiquement `AUDIT_MODE = INCREMENTAL_UPDATE`.
2. **Bypass des Posts Épinglés & Arrêt $K=2$ :** Les scanners sociaux inspectent les publications récentes, ignorent les posts épinglés sans incrémenter le compteur, et stoppent immédiatement le défilement dès que $K=2$ publications consécutives non épinglées sont déjà archivées.
3. **Suivi de Version & Notes Mobiles :** Les scanners de stores comparent la version avec `{known_version}` et calculent les deltas de volume et d'évaluation ($\Delta$).
4. **Deltas de Trajectoire d'Engagement ($\Delta$) :** Les publications majeures de la baseline sont réévaluées pour mesurer l'accélération virale ($\Delta$ réactions, $\Delta$ commentaires).
5. **Économie de Captures d'Écran :** Réutilisation des bannières et avatars existants si l'identité visuelle n'a pas changé. Zéro capture superflue.

---

## 📁 Architecture des Dossiers Hub & Spoke

Tous les livrables respectent une arborescence hermétique et modulaire :

```text
reports/
├── index.html                               # Cockpit Global & Répertoire des Marques
├── .gitkeep                                 # Maintient le dossier dans Git (vierge)
└── {slug}/                                  # Dossier Marque (ex: ag-be)
    ├── OVERVIEW.html                        # Hub Central : Reverse Brand Book Exécutif
    ├── STRATEGIC-AUDIT.html                 # Spoke : Critique Stratégique & Progression Scorecard
    ├── channels/                            # Spokes Plateformes (Rapports détaillés)
    │   ├── linkedin.html
    │   ├── instagram.html
    │   ├── tiktok.html
    │   ├── facebook.html
    │   ├── youtube.html
    │   ├── x.html
    │   ├── appstore.html                    # Spoke Mobile : Apple App Store
    │   └── playstore.html                   # Spoke Mobile : Google Play Store
    ├── assets/                              # Captures d'Écran Permanentes & Stylesheet
    │   ├── css/
    │   │   └── design-tokens.css
    │   ├── screenshot-hub-20260930.png
    │   └── ...
    └── markdown/                            # Source de Vérité IA (Archives Permanentes)
        ├── REVERSE-BRAND-BOOK.md
        ├── STRATEGIC-AUDIT.md
        └── channels/
            ├── linkedin.md
            ├── appstore.md
            ├── playstore.md
            └── ...
```

---

## 🎯 Barème Déterministe sur 10 Points

Toutes les évaluations utilisent l'échelle standardisée sur 10 points (interdiction absolue des lettres de notation américaines) :

$$\text{Score Global de Cohérence (/10)} = \frac{\text{P1 (ToV)} + \text{P2 (Dark Social)} + \text{P3 (Vélocité)} + \text{P4 (Conversion)}}{4}$$

- **Pilier 1 : Tonalité Réelle & Réception Communautaire (0–10) :** Cohérence des discours, ratio conversationnel (alerte si $< 0.5\%$), détection des débordements SAV. Plafonné à 6.5/10 si frictions non traitées, note mobile $< 3.0 / 5.0$, ou taux de réponse développeur aux avis critiques $< 20\%$.
- **Pilier 2 : Cohérence Omnicanale & Dark Social (0–10) :** Unité graphique, complétude Open Graph, simulation de partage privé (`RESOLVED` ou `FAILED`), cohérence éditeur store.
- **Pilier 3 : Vélocité de Publication & Cadence (0–10) :** Fréquence d'émission, mix de formats (% Reels/Shorts), vitalité des releases applicatives (mise à jour $< 45$ jours : bonus +0.5, $> 6$ mois : pénalité).
- **Pilier 4 : Conversion & Récit Produit (0–10) :** Optimisation des liens en bio, clarté des appels à l'action, bonus de conversion mobile (+0.5 pt si note $\ge 4.4 / 5.0$ et $\ge 1\text{M}+$ téléchargements), rigueur épistémique paid vs organic (`ad_badge_present`).

### Échelle Qualitative
- **8.0 – 10.0 / 10 :** *Excellence & Forte Cohérence* (`.score-high`)
- **6.0 – 7.9 / 10 :** *Cohérence Modérée en Consolidation* (`.score-medium`)
- **< 6.0 / 10 :** *Désalignement Critique* (`.score-low`)

---

## 🛡️ Sécurité Passive & Rigueur Épistémique

1. **Posture 100% Lecture Seule :** Les scanners explorent les plateformes en consultation passive. Aucune publication, aucun message, aucun envoi de formulaire, aucune modification externe.
2. **Rigueur Épistémique (Paid vs Organic) :** Zéro affirmation de campagnes publicitaires sans badge DOM natif (`ad_badge_present: true`). Toute anomalie de volume sans badge est qualifiée au conditionnel de *portée amplifiée estimée* avec mention méthodologique obligatoire.
3. **Hygiène des Chemins Locaux :** Aucun chemin absolu fuitant dans les livrables (`file:///Users/...`, `/var/folders/...`). Tous les liens et images utilisent des chemins relatifs propres au projet.

---

## 📄 Licence

Ce projet est distribué sous licence [Apache 2.0](LICENSE).
