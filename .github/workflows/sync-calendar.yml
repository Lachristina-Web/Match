# .github/workflows/sync-calendar.yml
# Planifie la synchronisation automatique toutes les 6h
# Dépose ce fichier dans ton repo GitHub à l'emplacement indiqué

name: Sync calendrier LA CHRISTINA → Framer CMS

on:
  schedule:
    # Toutes les 6h (00h, 06h, 12h, 18h UTC = 02h, 08h, 14h, 20h Paris)
    - cron: "0 */6 * * *"

  # Permet aussi de déclencher manuellement depuis GitHub Actions
  workflow_dispatch:

jobs:
  sync:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: "20"

      - name: Run sync script
        run: node sync-ics-framer.js
        env:
          # Ces variables remplacent les valeurs dans CONFIG du script
          # → Les ajouter dans Settings > Secrets and variables > Actions de ton repo
          FRAMER_API_KEY: ${{ secrets.FRAMER_API_KEY }}
          FRAMER_COLLECTION_ID: ${{ secrets.FRAMER_COLLECTION_ID }}
