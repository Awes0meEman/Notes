# Organization
1. We need a script that initializes a FSM within an object we intend to utilize an FSM with. For future reference sake, this will be something like `state_machine_init()`. It will need some of the following variables so we can use them later on:
	1. `state`: this variable will hold the script index for the current state. The script will have the code that will be run in the step event for this object.
	2. `state_next` When we switch states, we typically want to let the current state finish out this step before we switch, so when we call the script to switch states, we update this value, which will modify the state variable in the end step event.
	4. `state_timer` keeps track of how many steps you've been in the current state.
	5. `state_map` a DS that uses the state's name as a key and the script as a value
	6. `state_stack` a DS that keeps track of your state history
	7. `state_new` bool that is set upon transitioning into a new state that the script will check for to do any setup for the state that should only happen at the beginning of the state
	8. `state_var[0]` array that holds values for the duration 
	9. `state_can_interrupt` this is a boolean value that determines if a state can interrupt another state
	10. `state_is_invincible` bool that determines if a character is invincible during a state
	11. Add more state variables as needed if we find we need any
2. We need to create states through a state creation function that sets the variables we defined above. This would go in an object's create event.
3. We then need a function/script that executes our state's script during the step event. 
4. In our end step, we need a function that updates our state.
5. In our destroy step we need a function that runs our state's cleanup code, which should clean up our data structures we created 
   >[!note]
   >Most data structures aren't taken care of through the [[Garbage Collection]] system in GameMaker so we need to clear them out ourselves via their .destroy() method

6. We need a function to switch between states. This would update the `state_next` variable within our current state, which would then get picked up when we call our update function to switch to a new state.
7. We need a function that goes back to our previous state, in case our state gets interrupted and we need to go back to what we were doing before. We would use our `state_stack` variable to check for the most recent state before our current one, and queue that as our next state in `state_next`, so when we go to update our state again we will go back to our previous one.

https://www.reddit.com/r/gamemaker/comments/353aq6/tutorialexample_finite_state_machines_the_most/