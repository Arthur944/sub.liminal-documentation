# Spaced Repetition Algorithm
**Inputs**: _user_
* Get all concepts that need to be repeated (due date is sooner than now)
* Put them in a queue
* next():
	* if the maybe_wrong of the first concept in queue is False:
		* Find the cards that contain the first concept in the queue, and have the biggest number of concepts in the queue, but have no concepts that the users hasn't seen yet.
		*  Among these, find the ones that have the minimal number of concepts outside of the queue.
		*  Out of these, find the ones the user has seen a minimal number of times. 
		* Out of these, return on random.
	* if the maybe_wrong of the first concept in queue is True:
		* Find the card that has only one concept, the first one in the queue, and return it.
* answered(correct):
	*  If correct is True:
		* Remove the cards from the queue
		* Set their intervals to <br /> 
			$$
			interval = seconds \cdot learningRate
			$$
		where _seconds_ equals the amount of seconds since last_answered, and the learning rate is the learning rate set in _User_
	* If correct is False:
		* Gather up all the concepts in the card, and remove them from the queue
		* Collect their <i>UserConcept</i>s, and set maybe_wrong to True on each.
		* Insert all the concepts into the beginning of the queue.