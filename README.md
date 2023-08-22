class Character:
    def __init__(self, name, health, attack):
        self.name = name
        self.health = health
        self.attack = attack

    def take_damage(self, damage):
        self.health -= damage

class Enemy(Character):
    def __init__(self, name, health, attack):
        super().__init__(name, health, attack)

class Player(Character):
    def __init__(self, name):
        super().__init__(name, health=100, attack=10)
        self.inventory = []

    def pick_up_item(self, item):
        self.inventory.append(item)

class Item:
    def __init__(self, name, description):
        self.name = name
        self.description = description

class Room:
    def __init__(self, name, description):
        self.name = name
        self.description = description
        self.enemies = []
        self.items = []

    def add_enemy(self, enemy):
        self.enemies.append(enemy)

    def add_item(self, item):
        self.items.append(item)

class Game:
    def __init__(self):
        self.player = None
        self.current_room = None

    def start(self):
        self.create_game_world()
        self.player = Player(input("Enter your character's name: "))
        self.current_room = self.entrance

        print("Welcome to the RPG Game!")

        while self.player.health > 0:
            self.display_current_room()
            self.process_player_input()

        print("Game Over. You have been defeated.")

    def create_game_world(self):
        self.entrance = Room("Entrance", "You stand at the entrance of a dark cave.")
        # Define more rooms, enemies, and items

    def display_current_room(self):
        print(f"\n{self.current_room.name}")
        print(self.current_room.description)
        if self.current_room.enemies:
            print("Enemies in the room:")
            for enemy in self.current_room.enemies:
                print(f"- {enemy.name}")

    def process_player_input(self):
        action = input("\nWhat will you do? ")
        if action == "quit":
            exit()

        # Implement logic for movement, combat, item interactions, etc.

    # Implement more game mechanics, combat system, story progression, etc.

if __name__ == "__main__":
    game = Game()
    game.start()
