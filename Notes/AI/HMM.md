[[lecture20.pdf]]

- Temporal probabilistic model
- Hidden state vars: X_t at time t
- Evidence vars: E_t at time t
- Initial distribution: P(X_0)
- First-order Markov assumptions:
	- Transition: Next state only depends on the previous one.
	- Sensor: ...?
- Joint distribution: ...?
- The red states are hidden states, the blue ones are the evidence states that result:![[Screenshot 2025-03-27 at 8.47.03 AM.png]]
##### Filtering
Estimate the current state of the hidden variable from the sequence of all evidence.![[Screenshot 2025-03-27 at 9.06.51 AM.png]]![[Screenshot 2025-03-27 at 9.07.04 AM.png]]
... u can continue the process to calculate $P(H_2 | F, B)$

# Decision-making Under Uncertainty
Decision theory = Probability theory + Utility theory
![[Screenshot 2025-03-27 at 9.23.45 AM.png]]
- What action (a) can i take that will maximize expected utility, or (probability of being next state given current evidence * profitability of next state) ?

##### Decision Network
Three types of nodes:
- Chance (oval), Action (rectangle), Utility (diamond)
- Links connect action and chance to utility
- Find sequence actions that give Maximum Expected Utility (MEU)
- Value of Perfect Information (VPI)
	- = MEU(knowing the information) - MEU(not knowing it)
![[Screenshot 2025-04-01 at 12.35.22 AM.png]]
![[Screenshot 2025-04-01 at 12.35.41 AM.png]]
