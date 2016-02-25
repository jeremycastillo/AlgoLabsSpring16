# Lab 1 Report - Stable Matchings

##Part1: Write a report

###(a) Prove that there always exists a perfect matching that is weakly stable.

###(b) Give an algorithm in pseudocode to find a stable assignment.
	
	while there are freeTenants
		get first tenant from the list
		determine this tenant's highest apartment 
		if said apartment is available 
			match tenant to apartment
			remove this tenant from the freeTenants list
		else 
			determine landlord who owns this apartment
			determine current owner of this apartment
			compare preferences of the two tenants trying to get this apartment
			if landlord perfers this new tenant 
				unmatch current owner
				add current owner to free tenants list
				match this new tenant with apartment
				remove tenant from free tenants list
			endif
		endif
		mark highest apartment as being proposed to by this tenant
	endwhile

###(c) Give proof of algorithm's correctnes. Prove both that algorithm terminates and that it gives a correct result.
//perfect matching && weakly stable matching 

###(d) Give the runtime complexity of algorithm in Big-O notation.

Each iteration consists of a tenant trying to get an apartment, an apartment that he/she has not attempted to gain before. Let P(t) denote the set of pairs (T, A) such that T (tenant) has attempted to gain A (apartment) before the end of iteration t, for all t, the size of P(t+1) is greater than the size of P(t). There are only N^2 possible pairs of tenants and apartments in total, so the vaule of P(progress) can increase to at most N^2 times over the course of the algorithm. Hence N^2 iterations, thus O(N^2), where N is the number of tenants.

###(e) Give the runtime complexity of this brute force algorithm in Big-O notation and why.

The runtime complexity of the brute force algorithm is O(N!), where N is the number of tenants (number of tenants and apartments should be the same). With the brute force algorithm we compute every possible outcome and then see if a certain matching is weakly stable. There are N! possible matchings that can be made so it takes us O(N!) to actually make all the pairings. The reason that there are N! possible matchings is because when we pair a tenant and an apartment we care about every last detail. When forming all possible ways to match tenants and apartments we start talking about permutations. With permutations we care about every single detail since order matters.

###(f)  Plot the number of couples (x-axis) against the time in ms it takes for the code to run (y-axis). Have 8 points for GS algorithm and 4-8 points for the brute force method. Take note of the trend in run time as the number of apartments increases.
	![Brute Force Graph](../Lab1Charts/BrutoForce.png)
	![GS Graph](../Lab1Charts/GSSolution.png)
