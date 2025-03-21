# Combination Coherency (CC) Language Specification

## Overview
The **Combination Coherency (CC) Language** defines how entities interact, evolve, and behave across state-based systems using structured, narrative-friendly logic. It supports labeled groups, causal chaining, polymorphic scoping, and natural syntax for both machines and humans.

---

## 🔤 Syntax Primer

### 1. **Labeled Groups**
Use `label: (entities...)` to define reusable groups:
```
(visitor: alice, rabbit, cat)
(drink: potion, tea)
```

### 2. **Action Statements**
Express relationships and behaviors with one or more prepositions:
```
visitor.drinks drink --in container
visitor.eats food --on container --with eating_method
```

### 3. **Conditionals**
Trigger logic or transitions using double dash `--then` for clarity:
```
-> if visitor.drinks --then visitor.shrinks
```

### 4. **Nested Coherencies**
Define progression of logic:
```
shrinking {
  visitor.shrinks --to size
}
```

### 5. **Property Referencing**
Refer to labels dynamically:
```
visitor.opens size.sized (door, tunnel)
```

### 6. **Scoped Size-Based Behavior**
Use `label.sized entity.action target` to express state-specific behaviors.

---

## 🌌 Wonderland Example (Finalized with All Features)

```
CC {
  interaction {
    (visitor: alice, rabbit, cat)
    (drink: potion, tea, elixir)
    (magic_drink: potion, elixir)
    (food: mushroom, cake)
    (magic_food: mushroom, cake)
    (book: spellbook, riddle_scroll)
    (magic_book: spellbook)
    (container: cup, bottle, dish)
    (eating_method: fork, fingers, spoon)
    (portal: mirror, spiral_door, cloud_gate)
    (magic_pit: well, trench, cave, tube)
    (random_thought: mom, sister, rabbit, school, friends, games, fun, sad, happy)

    drinking {
      visitor.drinks drink --in container
      -> if visitor.drinks magic_drink --then visitor.shrinks
    }

    eating {
      visitor.eats food --on container --with eating_method
      -> if visitor.eats magic_food --then visitor.grows
    }

    reading {
      visitor.reads book
      -> if visitor.reads magic_book --then visitor.unlocks portal
    }

    shrinking {
      (size: bug, mouse, doll)
      visitor.shrinks --to size

      entry {
        bug.sized visitor.enters (ant_tunnel, root_gap) {
          visitor.explores (fungal_nest, leaf_network)
        }

        mouse.sized visitor.enters (mouse_hole, crack_in_wall) {
          visitor.explores (wall_vents, underfloor_paths)
        }

        doll.sized visitor.enters (dollhouse_door, bookshelf_gap) {
          visitor.explores (tiny_furniture, lost_jewels)
        }
      }
    }

    growing {
      (size: tall, huge)
      visitor.grows --to size

      smashing {
        visitor.breaks (door, ceiling, room) --from inside
      }
    }

    unlocking {
      visitor.unlocks portal
      portal.open --to (forest, desert, floating_island)
    }

    falling {
      visitor.falls (slowly, gracefully) --into magic_pit
      -> if visitor.falls --then visitor.wonders --about random_thought
    }
  }
}
```

---

## 🔍 Scoped Exploration Guide

### 🧠 Principle
> The moment an entity transitions state (e.g. shrinks), they enter a space consistent with that state and only explore what's inside that space.

---

### ❌ Anti-Pattern
```
visitor.enters entries
visitor.explores places
```
- Allows impossible combinations (e.g., bug exploring dollhouse)

---

### ✅ Correct Pattern
```
bug.sized visitor.enters (...) {
  visitor.explores (...)
}
```

- Entry is **scoped** to size
- Exploration is scoped **to the entry**

---

## 📐 Design Rule
> Exploration is a **child of entrance**, which is a **child of state change**.

This preserves:
- Temporal order
- Spatial logic
- Narrative believability

---

## 🧭 Summary

- Use `label: group` to reference entities
- Use `X.Y` for property references
- Use multiple prepositions as needed
- Use `--then` to improve conditional readability
- Avoid general access unless truly shared
- Use `label.sized subject.action` for scoped branching

The CC Language elegantly models how systems **change over time**, and how entities **interact conditionally**, based on what they are, what they do, and what they become.


---

## ⚠️ Clarification: Meaning of `-> if`

The `-> if` syntax denotes a **strict consequence**, not a possibility.

```
-> if visitor.eats magic_food --then visitor.grows
```

This means:
> If the visitor eats a magic food, they **must** grow — not *might* grow, or optionally grow. The effect is guaranteed.

This differs from **nesting**, which implies scope or possibility, but **not a requirement**:
```
visitor.shrinks {
  visitor.enters tunnel
}
```
> This means the visitor *may* enter the tunnel after shrinking — not that they *must*.

Always use `-> if ... --then ...` to denote **causal, mandatory outcomes**.
