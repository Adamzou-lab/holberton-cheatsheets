# Instructions — holberton-cheatsheets

## Quand un nouveau cheatsheet est ajouté

Dès qu'Adam mentionne l'ajout d'un nouveau cheatsheet, effectuer **dans cet ordre** sans attendre d'instructions supplémentaires :

### 1. Vérifications dans le fichier HTML du sheet

- [ ] `<link rel="stylesheet" href="../css/common.css">` présent dans le `<head>`
- [ ] Variables bridge définies dans `:root` (nécessaires pour que common.css fonctionne) :
  ```css
  --bg2:         <couleur de fond secondaire>;
  --primary:     <couleur neon principale du sheet>;
  --primary-rgb: <r, g, b de --primary>;
  ```
- [ ] Bouton HUB présent juste avant `</body>` :
  ```html
  <a class="hub-btn" href="../index.html">
    <span class="hub-icon">⌂</span>
    HUB
  </a>
  ```
- [ ] Footer GitHub présent dans `<footer>` :
  ```html
  <br><br><a href="https://github.com/Adamzou-lab" target="_blank" rel="noopener noreferrer" style="color:#4a6050; text-decoration:none; font-size:7px; letter-spacing:2px;">⌥ GITHUB — ADAMZOU-LAB</a>
  ```

### 2. Ajout de la carte dans index.html

Ajouter une `<a class="sheet-card">` avant `<div class="empty-state" id="empty">` en respectant :
- `href="sheets/nom_du_fichier.html"`
- `data-subject` cohérent avec une catégorie existante : `c-lang`, `security`, `algorithms`, `git`, `cs`, `terminal`, `devops`
- `data-id` unique
- `data-title` et `data-tags` descriptifs pour la recherche
- Icône, badge sujet + niveau, titre, description et topics adaptés au contenu

Si le `data-subject` n'existe pas encore comme filtre dans index.html, ajouter le bouton filtre correspondant dans `.filters-row` avec sa couleur propre (filtre + règle CSS `.sheet-card[data-subject="..."]`).

### 3. Déploiement SSH

```
sshpass -p 'M6HiIfM3TiKUJOzv' scp -o StrictHostKeyChecking=no -P 2008 \
  sheets/nom_du_fichier.html \
  root@dns.safa.hugochilemme.com:/var/www/cheatsheets/sheets/

sshpass -p 'M6HiIfM3TiKUJOzv' scp -o StrictHostKeyChecking=no -P 2008 \
  index.html \
  root@dns.safa.hugochilemme.com:/var/www/cheatsheets/
```

### 4. Commit & Push Git

```
git add sheets/nom_du_fichier.html index.html
git commit -m "Ajout nom_du_fichier + carte index.html"
git push
```

---

## Couleurs par catégorie

| data-subject  | Couleur    | Hex       | RGB          |
|---------------|------------|-----------|--------------|
| c-lang        | Violet     | `#b54eff` | 181,78,255   |
| security      | Rose       | `#ff2d78` | 255,45,120   |
| algorithms    | Jaune      | `#ffe600` | 255,230,0    |
| git           | Orange     | `#ff6b00` | 255,107,0    |
| cs            | Cyan       | `#00f5ff` | 0,245,255    |
| terminal      | Vert       | `#39ff14` | 57,255,20    |
| devops        | Bleu ciel  | `#00c8ff` | 0,200,255    |

## Infos serveur

- **SSH** : `ssh root@dns.safa.hugochilemme.com -p 2008`
- **Webroot** : `/var/www/cheatsheets/`
