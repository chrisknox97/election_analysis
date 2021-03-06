# PyPoll with Python

## Overview of Election Audit 

### To automate congressional voting tabulations for a Colorado district using Python, with the intent of using such methods on additional political elections. This specific audit to determine each participating candidate and county’s voter turnout, voter percentage, as well as the election winner and county with the highest turnout. 

## Election-Audit Results

### Counties

* **Total Votes Cast**

The total number of votes cast in this congressional election was 369,711. To tabulate this data using Python, the script needed to do the following:

	Initialize a Total Vote Count at Zero
	total_votes = 0

	Add each subsequent vote to the Total Vote Count
	total_votes = total_votes +1

	Print Total Votes to Terminal
	election_results = (
		f“\nElection Results\n”
		f“-----------------------------\n”
		f “Total Votes: {total_votes:,}\n”
		f“-----------------------------\n”)
	print(election_results, end=“”

* **County Votes & Percentages**

In this congressional election, the participating counties received the following voter counts and percentages: 


	Jefferson County: 38,855 Votes Cast (10.5% of Total Votes)

	Denver County: 306,055 Votes Cast (82.8% of Total Votes)

	Arapahoe County: 24,801 Votes Cast (6.7% of Total Votes)


To ascertain this data, I first needed to create a county list and county votes dictionary from which I could derive my data. As such I wrote the following Python script: 

	Create a County List
	counties = []
	
	Create a County Votes Dictionary
	county_votes = {}

After creating my list and dictionary, I needed to extract the county names from my ``csv``, check that all the counties that submitted votes in this election were represented in my ``counties`` list,and start calculating each county’s respective votes. I did this by writing the following ``if`` statement: 

	Extract County Name
	county_name = row[1]
	
	Create an If Statement if County Name Not Found in counties List
	if county_name not in counties:

	Add County To County List
	counties.append(county_name) 

	Track County Voter Counts
	county_votes[county_name] = 0

	Add Vote To Each County as It Appears
	county_votes = [county_name] += 1
	

Next, I needed to create a ``for`` loop, compiling all the county names participating in the election and assigning them their respective vote counts and vote percentages. The script to carry out these operations is listed below: 

	Start For Loop by Retrieving County Name From County Dictionary
	for county_name in county_votes:

	Get the County Vote Count
	votes = county_votes.get(county_name)

	Calculate the County Vote Percentage
	vote_percentage = float(votes) / float(total_votes) *100

	Print County Results to Terminal
	county_results = (
		f“{county_name}: {vote_percentage:.1f}% ({votes:,})\n”)

* **Largest County Turnout**

This election audit was also concerned about determining which county had the highest voter turnout. The result of this portion of the audit is listed below: 
	
	Largest County Turnout
	
	Winner: Denver
	Winning Vote Count: 306, 055
	Winning Percentage: 82.8%

To automate this task, I had to create ``Largest County Turnout`` as well as initialize my county votes and county winning percentages at zero. 

	Initialize Largest County Turnout as Open String
	largest_county_turnout  = “”
  
  	Initialize County Vote at Zero
	largest_county_vote = 0

	Initialize County Winning Percentage at Zero
	largest_county_percentage = 0

Next, I needed to write another ``if`` statement to compare each county’s voter turnout against winning parameters to determine which one had the highest turnout. 

	if (votes > largest_county_vote) and (vote_percentage > largest_county_percentage)
		largest_county_vote = votes
		largest_county_turnout = county_name
		largest_county_percentage = vote percentage

The winner is then printed to the terminal using the following portion of code:

	winning_county_summary = (
		f“--------------------------------\n”
		f“Largest County Turnout\n”
		f“\n”
		f“Winner: {largest_county_turnout}\n”
		f“Winning Vote Count: {largest_county_votes}\n”
		f“Winning Percentage: {largest_county_percentage}\n”
		f“--------------------------------\n”
	print(winning_county_summary)
	
### Candidates

* **Candidate Vote Counts & Percentages**

As it turns out, this congressional election was not particularly close with one candiate receiving nearly three-quarters of the vote. 

	Charles Casper Stockham: 85, 213 Votes Cast (23.0% of the Vote)

	Diana DeGette: 272, 892 Votes Cast (73.8% of the Vote)

	Raymon Anthony Doane: 11,606 Votes Cast (3.1% of the Vote)

The procedure for extracting this data was remarkedly similar to the code written to tabulate the county votes. 

	Initialize Candidate Options List and Candidate Votes Dictionary
	candidate_options = []
	candidate_votes = {}

	Extract the Candidate Name
	candidate_name = row[2]

	Add Candidate Name If Not Found in Candidate Options List
	if candidate_name not in candidate_options: 
		candidate_options.append(candidate_name)

		Start Counting Votes for Each Candidate
		candidate_votes[candidate_name] = 0
		candidate_votes[candidate_name] += 1

    Create a For Loop to Calculate Candidates’ Vote Count & Percentages
    for candidate_name in candidate_votes:
		votes = candidate_votes.get(candidate_name)
		vote percentage =float(votes) / float(total_votes) * 100

    Print Candidate Results to Terminal
    candidate_results= (
	    	f“{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n”)
    print(candidate_results)

* **Winning Candidate**

The winning candidate in this election was Diana DeGette, who received 272,892 votes or approximately 73.8% of the vote. The winning candiate was determed by comparing the ``winning_count`` and ``winning_percentage`` against the ``votes`` and ``vote_percentage`` respectively. As a result, the final printed results were achieved using the following script:
	
	Determine Winner
    	if (votes > winning_count) and (vote_percentage > winning_percentage)
		winning_count = votes
      		winning_candidate = candidate_name
      		winning_percentage =vote_percentage

	Print Winner to Terminal
	winning_candidate_summaery = (
		f“-------------------------------\n”
		f“Winner: {winning_candidate}\n”
		f“Winning Vote Count: {winning_count:,}\n”
		f“Winning Percentage: {winning_percentage:.1f}%\n”
		f“-------------------------------\n”)
	print(winning_candidate_summary)

## Election-Audit Summary

### This script could be used in additional congressional and senatorial campaigns as it can quickly tabulate votes received by candidates and by county with efficiency and accuracy when compared to hand counting. Should the Electoral Commission wish to use this script for future elections, its members can rest assured in its malleability.

* **Adding Counties**

Should this district's counties change due to redistricting measures in a future election cylce, a new county could easily be added to the script by simply amending the county list. 

	counties.append("New County Name")

* **Removing Candidates**

Similarly, should primary candidates need to be removed from the script for a general election; Python makes to process rather easy. 

	counties.remove("Old Candidate Name")

