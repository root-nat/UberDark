# 🍔 Dark Kitchen — Plateforme Multi-Restaurants (Style UberEats)

## Architecture

```
dark-kitchen-uberdark/
├── client/index.html          → 📱 App client multi-restaurants (PWA)
├── vendor/index.html          → 🏪 Espace vendeur (par restaurant)
├── admin-dashboard/
│   ├── index.html             → 📊 Admin global
│   └── kitchen.html           → 👨‍🍳 Interface cuisine tablette
├── onboarding.html            → 📝 Inscription nouveaux restaurants
├── backend/                   → API NestJS multi-restaurants
└── database/schema.sql        → Schéma MySQL multi-restaurants
```

---

## App Client — Parcours UberEats

1. **Accueil** — Recherche, filtres par cuisine, liste des restaurants avec ratings/délais/frais
2. **Restaurant** — Page dédiée avec banner, infos, menu organisé par catégories + tabs sticky
3. **Panier** — Par restaurant, barre progression livraison offerte, totaux
4. **Checkout** — Adresse, notes, paiement en espèces
5. **Suivi** — Temps réel Socket.io avec étapes animées + estimation

## Installation XAMPP

```powershell
# 1. Créer base "darkkitchen" dans phpMyAdmin
# 2. Importer database/schema.sql

# 3. Backend
cd backend && npm install && npm run start:dev

# 4. Ouvrir client/index.html dans le navigateur mobile
```

## Accès

| Interface | URL |
|-----------|-----|
| App Client | client/index.html |
| Espace Vendeur | vendor/index.html |
| Admin | admin-dashboard/index.html |
| Cuisine | admin-dashboard/kitchen.html |
| Onboarding | onboarding.html |
| API | http://localhost:3000/api/v1 |

## Nouveautés v2 (multi-restaurant)

- `restaurants` table avec owner_id, slug, rating, delivery_fee, free_delivery_over
- `products` et `categories` scoped par `restaurant_id`
- `orders` scoped par `restaurant_id`
- API `/restaurants` publique avec filtres (city, cuisine)
- `/restaurants/:slug` pour les pages restaurant
- Chaque vendeur gère ses propres produits/catégories
