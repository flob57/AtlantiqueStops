# Configuration Notion — AtlantiqueStops

AtlantiqueStops utilise le même principe que BreizhStops : le secret `NOTION_TOKEN` est conservé dans Cloudflare et les bases utilisées par l'application sont indiquées par leurs identifiants Notion. **Aucun fallback vers les bases générales « Bus et Cars / Bus Collection » ne doit être utilisé.**

## Parc Océcars

La base du parc préparée dans ton espace Notion est `Parc Océcars`.

- Base Notion : `https://app.notion.com/p/3c193645836180918c1ac73df7ea9eba?pvs=204`
- Identifiant de base à utiliser avec l'API : `3c193645-8361-8091-8c1a-c73df7ea9eba`
- Data source interne : `collection://3c193645-8361-80f4-84d7-000b045752c6`

Elle contient notamment :

- `Nom`
- `Immatriculation`
- `Statut`
- `Dépôt`
- `Exploitant`
- `Constructeur`
- `Modèle`
- `Fotobus`
- `Date d'arrivée`
- `Dernière affectation`

Le statut `En service` est celui utilisé pour identifier les véhicules actifs.

## Lignes Océcars

Une base `Lignes` existe également sous la page `Océcars - Transdev` :

`https://app.notion.com/p/3c1936458361805695f6ec61b8cc05c1`

- Identifiant de base : `3c193645-8361-8056-95f6-ec61b8cc05c1`
- Data source : `collection://3c193645-8361-80e1-b48c-000b93e6e644`

Elle est prévue pour la partie réseau / lignes.

## Yélo

La base `Parc Yélo` existe ici :

`https://app.notion.com/p/3b593645836180729babcf67ee4adfd8`

Elle pourra servir pour le parc Yélo et les données associées lorsque nous aurons défini précisément les bases à synchroniser.

## Prises de service / planning

Les bases de planning n'ont volontairement pas encore été renseignées dans AtlantiqueStops. Nous les configurerons lorsque tu auras choisi les bases de ton nouvel espace Notion destinées aux services de La Rochelle et de Charente-Maritime.

Variables Cloudflare prévues :

```text
NOTION_TOKEN
NOTION_PLANNING_DATABASE_ID
NOTION_LMJV_DATABASE_ID
NOTION_WEDNESDAY_DATABASE_ID
NOTION_SATURDAY_HOLIDAYS_DATABASE_ID
NOTION_PDVV_DATABASE_ID
NOTION_PARKING_DATABASE_ID
NOTION_TODO_DATABASE_ID
NOTION_WORKSHOP_DATABASE_ID
NOTION_SICKLEAVE_DATABASE_ID
NOTION_WORKS_DATABASE_ID
NOTION_VEHICLES_DATABASE_ID
```

Il est normal que plusieurs de ces variables restent vides pour le moment.

## Partage des bases

L'intégration Notion utilisée par `NOTION_TOKEN` doit avoir accès à chaque base réellement consommée par les routes Cloudflare.

Les bases identifiées aujourd'hui pour le 17 sont :

- `Parc Océcars` ;
- `Lignes Océcars` ;
- `Parc Yélo`.

Les autres bases seront ajoutées au fur et à mesure **uniquement lorsqu'elles auront été créées ou dupliquées dans l'espace Océcars**. Une variable absente doit produire une erreur de configuration ou désactiver proprement le module concerné ; elle ne doit jamais faire basculer l'application vers une ancienne base.
