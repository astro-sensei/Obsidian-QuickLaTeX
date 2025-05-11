# 📦 Obsidian LaTeX Renderer Plugin
**Plugin Obsidian avancé pour le rendu LaTeX (TikZ, pgfplots, tkz-tab...)**, avec compilation **offline via pdflatex** (si installé) ou **fallback online** (QuickLaTeX). Conçu pour la robustesse, la performance et la compatibilité multiplateforme (Windows, Linux, Mobile).

---

## ⚙️ Exigences & Cadre de Collaboration
### 🎯 Objectif
Ce dépôt contient le code complet, immédiatement exécutable, d’un plugin Obsidian respectant les plus hauts standards de qualité, selon les principes suivants :
### ✅ Qualité et Structure
- **Code prêt à l’emploi** : Aucun placeholder, tout est fonctionnel.
- **Architecture conforme Obsidian** : `main.ts`, `manifest.json`, `compiler/`, `utils/`, etc.
- **Testé** sur **Windows**, **Linux** et **mobile**.
- **Documentation JSDoc complète** pour toutes les fonctions critiques.
- **80% du livrable est du code** clair, commenté, copiable immédiatement.
- **Tests unitaires** inclus pour les composants sensibles (ex: compilation, cache).
---
## 🧠 Bonnes Pratiques
- **Réutilisation intelligente** : Ce plugin s’appuie sur des bases éprouvées comme [Obsidian-TikZJax](https://github.com/argitvigh/obsidian-tikz), tout en les modernisant.
- **Factorisation** : Pas de duplication inutile. Les logiques communes (hash, parsing, logs) sont centralisées.

---

## 📌 Fonctionnalités
### 🚀 Rendu LaTeX offline/online
```tikz
\begin{document}
% Ton code LaTeX ici (ex: \begin{tikzcd} ...)
\end{document}
```
- **Compilation Offline** :
	- Utilisation locale de `pdflatex` (via MikTeX/TeXLive).
	- Conversion en SVG via `pdf2svg` ou `dvisvgm`.
	- Fallback si `pdf2svg` indisponible.
- **Compilation Online** :
	- Appel sécurisé à [QuickLaTeX](https://quicklatex.com) (avec timeout configurable).

### ⚙️ Gestion des dépendances

- **Détection automatique** des packages requis.
- **Avertissement clair** si un package est manquant :  
	*Ex : "Package `tkz-tab` non installé. Requiert : `tcolorbox`, `tikz`..."*

### 📦 Cache intelligent

- **SVG mis en cache** localement.
- **Hash du code LaTeX** pour éviter recompilation.
- **Invalidation automatique** si modification.

### 🔐 Sécurité & Robustesse

- **Sandbox pdflatex** (process isolé).
- **Messages d'erreurs clairs** :
	- "pdflatex introuvable"
	- "Échec de la compilation : délai dépassé"
- **Logs** détaillés (mode debug activable).

---

## 🧰 Paramètres & UI

- Chemin personnalisé vers `pdflatex`
- Timeout pour QuickLaTeX
- Mode "offline uniquement"
- Onglet de statut dans les réglages :
	- Mode actif (offline/online)
	- Version détectée de `pdflatex`

---

## 🏗️ Arborescence du Code
```
MyLatexPlugin/
├── main.ts
├── settings.ts
├── compiler/
│		├── OnlineCompiler.ts
│		└── OfflineCompiler.ts
├── utils/
│		├── CacheManager.ts
│		└── DependencyParser.ts
├── styles.css
├── manifest.json
├── package.json
├── tsconfig.json
└── types.ts
```

---

## 📦 Installation
### 1. Dépendances système
- Installez **MikTeX v23+** ou **TeXLive 2023+**
- Assurez-vous que `pdflatex` est accessible via la ligne de commande
- Installez les outils nécessaires :
```bash
sudo apt install pdf2svg
# ou dvisvgm selon config
```
### 2. Dépendances Obsidian
- Ce plugin utilise TypeScript et Node.js :
```bash
npm install
npm run build
```
### 3. Paramétrage
- Dans Obsidian :
	- Activez le mode développeur
	- Chargez le plugin depuis le dossier `MyLatexPlugin/`
	- Dans les paramètres :
		- Configurez le chemin vers `pdflatex`
		- Définissez un timeout (ex: 3000 ms)

---

## 🧪 Test & Validation
- Utilisez le script d’installation de dépendances :
```bash
./install_tikz_dependencies.sh
```
- Testez dans un vault avec des blocs LaTeX variés :
	- Tableaux de variation
	- Arbres binaires
	- Graphes orientés (TikZ)
	- Pgfplots & tkz-tab

---

## 🗂️ Ressources
- 🔗 [Obsidian-TikZJax (GitHub)](https://github.com/argitvigh/obsidian-tikz)
- 🔗 [QuickLaTeX API](https://quicklatex.com/api.html)
- 📘 MikTeX : [https://miktex.org](https://miktex.org)

---

## ✅ Livrables inclus

- Code complet (100% des fichiers)
- README avec guide d’installation
- Commentaires JSDoc
- Script shell de setup (`install_tikz_dependencies.sh`)
- Couverture de test > 80% pour :
	- `compileToSVG()`
	- `CacheManager`
	- `DependencyParser`

---

## 📩 Feedback & Collaboration

- Un **vault de test** avec 20+ cas réels est fourni.
- Suggestions techniques bienvenues : performances, sécurité, architecture.

---

## 🚫 Interdits

- ❌ Aucune fonction incomplète (`// TODO`)
- ❌ Aucun exemple non fonctionnel
- ❌ Aucune documentation manquante sur les méthodes critiques

---

## 🧠 À propos

Ce plugin est conçu pour des utilisateurs avancés (professeurs, chercheurs, étudiants en maths/physique), avec un **besoin de rendu LaTeX fiable et puissant dans Obsidian**, même **hors ligne**.
