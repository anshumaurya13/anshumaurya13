 GitHub prokclass TileSwapGame:
    def __init__(self):
        self.root = (link unavailable)()
        self.root.title("Tile Swap Game")
        self.frame = tk.Frame(self.root)
        self.frame.pack()

        self.tiles = list(range(1, 16)) + [0]
        shuffle(self.tiles)
        self.tile_buttons = []

        for i in range(16):
            button = tk.Button(self.frame, text=str(self.tiles[i]), command=lambda i=i: self.swap_tile(i))
            button.grid(row=i//4, column=i%4)
            self.tile_buttons.append(button)

    def swap_tile(self, i):
        if self.tiles[i] == 0:
            return

        # Find adjacent tiles
        adjacent_tiles = []
        if i > 3:
            adjacent_tiles.append(i-4)
        if i < 12:
            adjacent_tiles.append(i+4)
        if i % 4 > 0:
            adjacent_tiles.append(i-1)
        if i % 4 < 3:
            adjacent_tiles.append(i+1)

        # Swap tile with adjacent tile
        for j in adjacent_tiles:
            if self.tiles[j] == 0:
                self.tiles[i], self.tiles[j] = self.tiles[j], self.tiles[i]
                self.tile_buttons[i].config(text=str(self.tiles[i]))
                self.tile_buttons[j].config(text=str(self.tiles[j]))
                return

    def run(self):
        self.root.mainloop()

if __name__ == "__main__":
    game = TileSwapGame()
    game.run()
```
