# 📘 Guide de Conventions pour les Donjons Skript

## 🧱 Structure Générale

Les donjons sont divisés en plusieurs **salles** (room1, room2, etc.).  
Chaque salle contient des **spawners** pour différents types de mobs, activés/désactivés dynamiquement selon la progression.

---

## 📛 Conventions de Nommage

### 🔹 Format pour les Spawners

```
<room>_<mob>
```

**Exemples :**
- `room1_SkPack_Warrior`
- `room2_SkPack_Archer`
- `room3_SkPack_Necromancer`

---

## ⚙️ Déclaration des Spawners dans les options

Chaque spawner doit être défini avec les paramètres suivants :

```skript
spawner_<room>_<mob>_create: mm spawners create <room>_<mob> <mob> <coords>
spawner_<room>_<mob>_cooldown: mm spawners set <room>_<mob> cooldown <value>
spawner_<room>_<mob>_range: mm spawners set <room>_<mob> activation_range <value>
spawner_<room>_<mob>_radius: mm spawners set <room>_<mob> radius <value>
spawner_<room>_<mob>_max_mobs: mm spawners set <room>_<mob> max_mobs <value>
spawner_<room>_<mob>_remove: mm spawners remove <room>_<mob>
```

🔧 **Exemple complet :**

```skript
spawner_room1_SkPack_Warrior_create: mm spawners create room1_SkPack_Warrior SkPack_Warrior world_dungeons,79,-49,27
spawner_room1_SkPack_Warrior_cooldown: mm spawners set room1_SkPack_Warrior cooldown 5
spawner_room1_SkPack_Warrior_range: mm spawners set room1_SkPack_Warrior activation_range 30
spawner_room1_SkPack_Warrior_radius: mm spawners set room1_SkPack_Warrior radius 10
spawner_room1_SkPack_Warrior_max_mobs: mm spawners set room1_SkPack_Warrior max_mobs 5
spawner_room1_SkPack_Warrior_remove: mm spawners remove room1_SkPack_Warrior
```

---

## 📦 Variables Globales

Les variables doivent suivre une convention claire :

```skript
{open_room<room_number>_dungeon_normal_<type>}
{count_<mob>_dungeon_normal_<type>}
{player_dungeon_normal_<type>::*}
```

**Exemples :**

```skript
{open_room1_dungeon_normal_skeleton}
{count_SkPack_Warrior_dungeon_normal_skeleton}
{player_dungeon_normal_skeleton::*}
```

---

## 🧠 Placeholder de Statut Visuel

À utiliser pour afficher l'état du donjon dans les interfaces ou messages :

```skript
# ─── Statut du Donjon ───────────────────────────────────────────
set {message_open_dungeon_normal_skeleton} to "&aOuvert"
set {message_open_dungeon_normal_skeleton} to "&cFermer"
```

---

## ✅ Bonnes Pratiques

- ✅ Toujours vérifier si une variable **n’est pas définie** avant de l’utiliser :  
  `if {var} is not set: set {var} to <value>`
- ✅ Utiliser `loop {player_dungeon_normal_skeleton::*}` pour les actions en groupe.
- ✅ Utiliser `wait 20 ticks` entre les transitions de salles.
- ❌ Ne jamais utiliser `variables:` en haut du script.
- ❌ Ne jamais utiliser `or` ou `and` : préférer **plusieurs blocs `if` séparés**.
- ❌ Ne pas utiliser `player` directement dans les variables (toujours par UUID ou listes séparées).

---

## 🚀 Création d’un nouveau Donjon

1. **Choisir un nom unique** (ex: `zombie`, `golem`, `inferno`)
2. **Créer les spawners dans les options** avec `room1`, `room2`, etc.
3. **Ajouter une commande `/dungeons <nom>` avec les sous-commandes**
4. **Suivre la logique d’activation/désactivation des spawners**
5. **Respecter toutes les conventions ci-dessus**
