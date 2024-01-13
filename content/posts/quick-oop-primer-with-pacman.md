---
title: "Extremely Quick Pacman-based OOP Primer"
date: 2024-01-12T18:08:40-05:00
draft: false
---

I have a friend who wanted to have a quick idea about whether he
should use classes and objects for his project. Of course I told him
that it depends.. on many aspects. He says that he doesn't really like
tutorials, so here I want to propose something more compact: the
skeleton of a Pacman game, just the most basic concepts, without any
bells and whistles (so of course not playable, although almost
runnable).

The reason for this choice is simple: a game is, I would say, the
quintessential type of application that benefits from being designed
from an OOP perspective, simply because the notion of objects in it is
usually very natural and intuitive.

So without further ado, here is an hopefully self-explanatory OOP
primer as a Pacman skeleton codebase:


```python
class Pacman:
    def __init__(self):
        g1 = Ghost("Blinky", "red", self) # instance of Ghost class
        g2 = Ghost("Pinky", "pinky", self) # another instance..
        g3 = Ghost("Inky", "cyan", self)
        g4 = Ghost("Clyde", "orange", self)
        self.ghosts = [g1, g2, g3, g4] # list of instances for easier manip
        self.player = Player(self) # single instance of Player class
        self.n_remaining_power_pellets = 4
        self.n_remaining_dots = 240

    def play(self):
        # Main game loop!
        while self.player.is_alive:
            self.player.update_position()
            for g in self.ghosts:
                g.update_position()
            self.detect_collisions()
            if self.n_remaining_dots == 0:
                break # Player won!

    def detect_collisions(self):
        for g in self.ghosts:
            if g.pos == self.player.pos:
                if self.player.is_invicible:
                    # ghost is eaten
                    self.ghosts.remove(g)
                else:
                    # player dies
                    self.player.is_alive = False
                    break

class Entity:
    def __init__(self, x0, y0, game):
        # variables which are common to all classes deriving from Entity
        self.pos = [x0, y0]
        self.game = game # instance of Pacman class

class Ghost(Entity):
    def __init__(self, name, color, game):
        self.name = name
        self.color = color
        super().__init__(20, 20, game) # call Entity's constructor

    def update_position(self):
        # Update self.pos randomly
        pass

class Player(Entity):
    def __init__(self, game):
        self.is_alive = True
        self.is_invincible = False
        super().__init__(10, 10, game) # c all Entity's constructor

    def update_position(self):
        # Check input controls to get new player position
        # Check if on a power pellet do:
        #    self.is_invincible = True
        #    self.game.n_remaining_power_pellets -= 1
        # Check if on a dot, do: self.game.n_remaining_dots -= 1

if __name__ == "__main__":
    game = Pacman()
    game.play()
    print("Game Over!")
```
