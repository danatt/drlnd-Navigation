**About the Task:**
    The Task is to collect as many yellow bananas as possible in a certain time and avoid the blue ones.
    Although the Game is 3-D, the Task takes basically  place in a 2-D environment. One can express the same
    task in the game viewed from above (GTA-Style). What makes the task perfect for a newbies-project is, that is isn't
    overly complex. The Agent has to learn one thing. Finding the banana next to it and move in its direction.
    The Agent could alternatively learn to prioritize a group of yellow fruits over a simple one right next to it, but 
    let's leave that out for now.
	
**About the Agent:**
	To solve this task, I used a "basic" version of DQN. I then implemented other extensions of DQN like Double DQN and 
	added Prioritized Experience Replay to test their influence. I couldn't notice to much of a difference, except for 
	a much longer computation time. I think that is because the task is easy enough.
	

**DQN Hyperparameters:**

	BUFFER_SIZE = int(1e5)  # replay buffer size
	BATCH_SIZE = 64         # minibatch size
	GAMMA = 0.99            # discount factor
	TAU = 1e-3              # for soft update of target parameters
	LR = 5e-4               # learning rate 
	UPDATE_EVERY = 4        # how often to update the network
	
	
* **DQN NN-Arch:**
	* hidden Layer 1 = 64 units  +relu activation
	* hidden Layer 2 = 64 units  +relu activation
	* loss = MSE


* **Ideas for Future Work:**
	* Implement Rainbow-Version of DQN.
	* Use a CNN Architecture to learn the Value-Function from raw pixel input.
	
	
**Results:**
	
	basic DQN:
		eps_start=1.0, eps_end=0.01, eps_decay=0.995
		Environment solved in 524 episodes!	Average Score: 13.10
		scores leveled out @ ~ 15,5 (1000 episodes)
		
	Double DQN:
		eps_start=1.0, eps_end=0.01, eps_decay=0.995
		Environment solved in 502 episodes!	Average Score: 13.01
		scores leveled out @ ~ 14.7 (1000 episodes)
		comment: took longer, but much more steady growth of Average Score
		
	basic DQN (+Prioritized Experience Replay):
		eps_start=1.0, eps_end=0.01, eps_decay=0.995
		Environment solved in 551 episodes!	Average Score: 13.01
		scores leveled out @ ~ 14.9 (1000 episodes)
		comment: much longer computation time, less influence on performance
