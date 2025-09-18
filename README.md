# Legit-Voting
The electronic voting machine is an electronic device used for casting and counting votes and displaying number of votes. in this project verilog is used to code and Nexys 4 FPGA is used to implement verilog code.
4 push buttons are used for voters to cast their votes. LEDs are used to represent the candidate whose button is pressed. 8 LEDs are used to represent number of votes casted.

## INPUTS:

reset

push buttons: one button for each candidate to accept votes.

mode: Handled by poling officer. If mode is low voter can cast vote and if mode is high, same push buttons can be used to see number of votes casted to the corresponding candidate.

authentication: Here this is an external input to this module. 
This can be given by poling officer or some other module can be used for authentication and that output can be routed to this module as input.

## OUTPUTS:

4 leds: These leds indicate which candidate's button is pressed.

person_voted led: this indicates whether the vote is casted or not. 

vote_count: This reg is to show vote count of each candidate based on the push button input when mode is high.

    
A person can cast vote when mode is low and authentication is high and reset is low. 
Vote is considered valid if the push button is pressed for atleast one second and no other push buttons are pressed at the same time.
"validation" module is used to check whether button is pressed for atleast one second.
Then that valid vote is counted to the corresponding register of the candidate.
Authentication should be made zero by poling officer to make sure that one person do not cast more than one vote as soon as the person casted their vote. This is indicated by
person_voted LED. This LED becomes low when authentication is made low and glows again when another valid vote is detected.
All this things are done when mode is low.

When mode is high, validation module works the same, but votes are not counted. Instead, number of votes of the corresponding candidate are shown at vote_count register.





