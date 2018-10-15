The Problem:
Given a number of steps, determine how many ways there are of taking them where each segment can take one or two steps together. Phase 1: simply print how many options there are. Phase 2: print out what the options are.

Solution:
We discovered that the number of options follows the fibonnacci sequence. Thus, for phase 1, we want to return the entry in the fibonacci sequence corresponding with the number of steps. To avoid calculating each entry too many times, we create a generator, and call it until it returns the correct entry. We keep the function which calls the generator seperate from the generator so we can use it for similar problems (e.g., phase 2).

for phase 2, we take a similar approach of building up the possibilities from an initial possibility where there is 1 step and thus one has one option: to take one step. Each time we increase the number of steps by one, we then produce an initial set of options which are identical to our previous set, but taking one additional step at the end. We then find which of our options now end in taking one step twice in a row, and create options identical to them, but ending in taking two steps once, instead of one step twice. We use a generator for this, again, which yields the set of options available for each number of steps. We then use the function from phase 1 to find the call we are interested in.

Further Thoughts:
Our current solution assumes we are only interested in keeping one solution, and that we will not be interested in the series leading to the solution. If we wanted the series, we would call the generators and feed the results into an array as we obtained them. When we wanted a particular entry, we would then check that we had not already found it in the generator, retrieving it from the array if we had. 

The solutions to phase 2 are presented as strings of 1s and 2s. This might not be the form we need the information in, however. We could present the solutions as arrays of 1s and 2s, working similarly. Instead of locating where the string ended in '11', we would find where the array's last two entries were both equal to 1 and replace the pair with a single entry equal to 2. This would be more likely to cooperate with a function ignorant of the origin of the data, which might expect an array rather than a string.

I am wondering if there is a more efficient way of solving phase 2 which would avoid passing through the options for taking fewer steps to reach the options for taking the number of steps we are interested in.