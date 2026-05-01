# cephtrainer-licenses

Registro delle licenze e License Manager per **CephTrainer**.

Sistema indipendente da `cephanalysis-licenses`: chiavi con prefisso `TRAIN-`, repo, JSON, dominio Vercel separati.

## Componenti

| File | Scopo |
|---|---|
| `cepht-licenses.json` | Registro source-of-truth. Modificato solo dal License Manager via Vercel function. |
| `index.html` | License Manager (admin UI). Login con GitHub PAT. |
| `train-license-check.js` | Script client incluso nelle pagine di CephTrainer. Mostra modal di attivazione, valida, registra device. |
| `api/register-device.js` | Vercel serverless function: aggiunge un browserId all'array `devices` di una licenza. |

## Variabili d'ambiente Vercel

Da impostare nel progetto Vercel (Production + Preview):

```
GITHUB_TOKEN  = ghp_...           # PAT con scope repo
GITHUB_OWNER  = odontoiatriamonaco
GITHUB_REPO   = cephtrainer-licenses
GITHUB_FILE   = cepht-licenses.json
```

## Deploy

Push su GitHub → Vercel deploya automaticamente.

- Manager admin: https://cephtrainer-licenses.vercel.app/
- Endpoint registrazione: https://cephtrainer-licenses.vercel.app/api/register-device
- JSON pubblico (lettura): https://raw.githubusercontent.com/odontoiatriamonaco/cephtrainer-licenses/main/cepht-licenses.json

## Tipi di licenza

| Tipo | PC ammessi | Scadenza tipica |
|---|---|---|
| `trial` | 1 | 1 mese |
| `standard` | 1 | 12 mesi |
| `pro` | 3 (configurabile) | 12 mesi |
| `lifetime` | ∞ | mai |
| `group` | N (configurabile, es. 30) | 6-12 mesi |
