# loopya-cron

Pinger gratuit pour Loopya. Il appelle **`loopya-feed-cron`** toutes les **15 minutes**
(le plan Vercel Hobby ne permet qu'1 cron/jour — voir `.github/workflows/ping.yml`).

Pourquoi : le feed v-tools ne garde que ~100 annonces ; à plus de 100 annonces/h,
sa fenêtre se vide en moins d'une heure. Poller toutes les 15 min évite de rater
les annonces (et donc les liens cop → achat) entre deux passages.

## Activation (1 seul geste)
Ajouter le secret `CRON_SECRET` au repo :
**Settings → Secrets and variables → Actions → New repository secret**
- Name : `CRON_SECRET`
- Secret : *(la valeur de `CRON_SECRET` lue dans Vercel → Project → Settings → Environment Variables)*

Puis onglet **Actions → ping-loopya-feed → Run workflow** pour tester (doit finir en vert).

Rien d'autre à maintenir : `keepalive.yml` garde les workflows actifs.
