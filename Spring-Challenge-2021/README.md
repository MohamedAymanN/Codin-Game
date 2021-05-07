# Game Rules

 - The game is played over several rounds called **days**. Each day can be made up of several game turns. On each turn, both players perform one action **simultaneously**.

## Forest
 - The forest is made up of **37 hexagonal cells**, arranged to form a **larger hexagon**.
 - Each cell has an **index** and up to **six neighbors**.
![image](https://user-images.githubusercontent.com/45315180/117443301-407e9900-af38-11eb-84a9-3bee20904cd6.png)

 - Dis(cell_a, cell_b) = min number of cells between them
 - Each cell may contain a tree. Each tree is owned by one of the players and has a size:
   - 0 for a seed.
   - 1 for a small tree.
   - 2 for a medium tree.
   - 3 for a large tree.
- Each cell has a richness which can be:
  - 0 for unusable cells. Nothing can grow on them.
  - 1 for low quality soil.
  - 2 for medium quality soil.
  - 3 for high quality soil.

## Days
 - At the start of each day, players receive sun points.
 - The day ends when both players stop taking actions.

## Sun & Shadows
 - Each tree casts a shadow that affects a number of cells based on its size:
  - Size 1 trees cast a shadow 1 cell long.
  - Size 2 trees cast a shadow 2 cells long.
  - Size 3 trees cast a shadow 3 cells long.
- The direction of a shadow depends on which direction the sun is currently pointing towards.
- On day 0, the sun is pointing towards direction 0, meaning all shadows are being cast to the right.

- In between each day, the sun moves to point towards the next direction, coming back to 0 after passing 5.
- The sun's direction will therefore always be equal to the **current day modulo 6**.

They will find the shadow on a cell spooky if any of the trees casting a shadow is of equal or greater size than the tree on that cell.

## Sun Points
 - The forest's lesser spirits will harvest sun points from each tree that is not hit by a spooky shadow.
 - The number of sun points harvested depends on the size of the tree:
   - A size 0 tree (a seed): no points.
   - A size 1 tree: 1 sun point.
   - A size 2 tree: 2 sun points.
   - A size 3 tree: 3 sun points.

## Actions
- After collecting sun points, both players take simultaneous turns performing one of four possible actions.
- As long as you have enough sun points, you can take any number of actions.
- The possible actions are:
   - SEED: Command a tree to eject a seed onto a cell within distance equal to the tree's size.
   - GROW: Command a seed or tree to grow into the next size. Trees can grow up to size 3 .
   - COMPLETE: Command a tree to complete its lifecycle. This removes the tree from the forest and scores you points. More information about points further down.
   - WAIT: Spend the rest of the day asleep. When both players are asleep, a new day begins and the players are awoken.
- **Any tree impacted by one of your actions becomes dormant for the rest of the day. A dormant tree cannot be the subject of an action.**

## Seed action
- To perform a seed action, you must pay sun points equal to the number of seeds (size 0 trees) you already own in the forest.
- You may not send a seed onto an unusable cell or a cell already containing a tree.
- Performing this action impacts both the source tree and the planted seed. Meaning both trees will be dormant until the next day.
- If both players send a seed to the same place on the same turn, neither seed is planted and the sun points are refunded. The source tree, however, still becomes dormant.

## Grow action
- Growing a seed into a size 1 tree costs 1 sun point + the number of size 1 trees you already own.
- Growing a size 1 tree into a size 2 tree costs 3 sun points + the number of size 2 trees you already own.
- Growing a size 2 tree into a size 3 tree costs 7 sun points + the number of size 3 trees you already own.

## Complete action
- Completing a tree's lifecycle requires 4 sun points.
- You can only complete the lifecycle of a size 3 tree.
- The forest starts with a nutrient value of 20.
- Completing a tree's lifecycle will award you with as many points as the current nutrient value + a bonus according to the richness of the cell:
   - 1: +0 points.
   - 2: +2 points.
   - 3: +4 points.
- Then, the nutrient value is decreased permanently by 1.

## Game end
- The game lasts the time it takes for the sun to circle around the board 4 times. This means players have 24 days to play.
- Players gain an extra 1 point for every 3 sun points they have at the end of the game.
- If players have the same score, the winner is the player with the most trees in the forest. Note that a seed is also considered a tree.

## Details
- Players start the game with two size 1 trees placed randomly along the edge of the grid.
- Players that are asleep do not receive input.
- If both players complete a lifecycle on the same turn, they both receive full points and the nutrient value is decreased by two.
- The nutrient value cannot drop below 0.
