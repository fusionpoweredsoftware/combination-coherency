# Combination Coherency Language (CCL)

**A declarative language for modeling coherent interaction logic, possibility spaces, and state transitions in world-building and narrative systems.**

---

## ✨ Overview

**Combination Coherency (CC)** is a semantic modeling language designed to define what is *logically possible* in a given world, rather than what *happens*. It provides a clear, structured way to express how entities relate, transform, and interact — all while enforcing coherency and preventing contradictions.

> CC is not a story scripting language. It is a logic framework that defines the combinatorial structure of a world.

---

## 🧠 Why CC?

Traditional narrative tools mix logic with dialogue, prose, or scene content. CC separates **what can happen** from **how it's described**, enabling:
- Coherent world modeling
- Dynamic interaction systems
- Modular logic reuse
- Possibility mapping across time, state, and scale

---

## 📘 Key Features

- **Declarative Syntax** — readable, writable, and composable
- **Polymorphic Scoping** — actions that adapt to state (e.g., size)
- **Strict Causal Logic** — `-> if A --then B` means *B must happen if A happens*
- **Scoped Nesting** — keep state and consequences tightly linked
- **Multi-Preposition Combinations** — model complex interactions cleanly

---

## 🔤 Example

```plaintext
CC {
  interaction {
    (visitor: alice, rabbit, cat)
    (drink: potion, tea)
    (magic_drink: potion)
    (container: cup, bottle)

    drinking {
      visitor.drinks drink --in container
      -> if visitor.drinks magic_drink --then visitor.shrinks
    }

    shrinking {
      (size: bug, mouse)
      visitor.shrinks --to size

      entry {
        bug.sized visitor.enters (ant_tunnel, root_gap) {
          visitor.explores (fungal_nest, leaf_network)
        }
      }
    }
  }
}
```

---

## 🧭 Use Cases

- 🔗 Narrative logic & interactive fiction world modeling
- 🎮 Game engines that require structured, branching logic
- 🧬 AI planning & simulation environments
- 🧠 Educational tools for teaching logic or event causality
- 📚 Worldbuilding databases & sandbox design systems

---

## 📁 Repository Structure

```
spec/           # Formal language specification
examples/       # Full CC examples like 'Wonderland'
parser/         # (Optional) CC interpreters, validators
```

---

## ⚠️ Philosophy of Causality

The CC language distinguishes between:
- **Possibility** (what *can* happen — modeled via nesting)
- **Causality** (what *must* happen — modeled via `-> if ... --then ...`)

This strict boundary helps authors build logical systems free from contradiction.

---

## 📄 License

MIT (you may reuse, adapt, and build upon it freely)

---

## ✍️ Author

Design, syntax, and structure by Fusion Powered Software

Want to build tools or help test? Reach out!


### 📄 File Extension

All CC language files use the `.ccl` extension:
- `example.ccl`
- `wonderland.ccl`
