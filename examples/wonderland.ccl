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
