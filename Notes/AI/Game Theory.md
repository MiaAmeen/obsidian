[[lecture08.pdf]]
- competitive multi-agent environment
- deterministic vs stochastic, has n players, win-win vs zero-sum, partially vs fully observable (perfect information), etc

Example: deterministic, two-player, turn taking, perfect information, zero sum game:
- s_0 : initial state
- to-move(s): player to move in state s
- actions(s): legal moves in state s
- result(s, a) {return s}: transition model
- is-terminal(s) {return bool}: if true, game over in s
- utlity(s, p): value of s to player p
#### Minimax Search
- state space search tree. players alternate turns.
- compute each node's minimax value:
	- best achievable utility assuming both players are rational
![[Screenshot 2025-02-01 at 8.43.44 PM.png]]
- Time: O(b^m)
- Space: O(bm)
#### Tree Pruning
![[Screenshot 2025-02-01 at 8.47.46 PM.png]]

##### Alpha-Beta Pruning
![[Screenshot 2025-02-05 at 6.48.50 PM.png]]
jesus christ

### Multiplayer Games
- States have utility tuples now. 
- Each player maximizes its own utlity; no longer zero sum
- Requires a generalized minimax search
![[Screenshot 2025-02-05 at 6.58.08 PM.png]]

