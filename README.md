
           
1.3.9
# Mr Froman is a God and Shall be Worshipped by All Mankind

So everyone knows how all of our code was deleted yesterday right?  Yea so I went through, found an older copy, and replaced all of the deleted code I could.  I do not know why it now shows up as a website, but when you go into the editor all is well.  It shows your code correctly spaced, even if it does not in the GitHub preview.  I hope that what I did here was useful, because it was all I could think of to do.  (I had to rewrite all of our teams code.)  oof.  (;;)  


from future import print_function

''' PrisonerDilemma.py allows hard-coding different strategies for the Iterative Prisoners Dilemma, the canonical game of game-theory. Each strategy plays 100 to 200 rounds against each other strategy. The results of all previous rounds within a 100-200 round stretch are known to both players.

play_tournament() executes the tournament and stores output in tournament.txt

Players should each code their strategies in their assigned section of code.

Aggregated results are stored in tournament.txt

Unpublished work (c)2013 Project Lead The Way CSE Project 1.3.5 Collaborating on a Project Draft, Do Not Distribute Version 8/23/2013 '''

import random def play_round(player1, player2, history1, history2, score1, score2): ''' Calls the get_action() function which will get the characters 'c' or 'b' for collude or betray for each player. The history is provided in a string, e.g. 'ccb' indicates the player colluded in the first two rounds and betrayed in the most recent round. Returns a 4-tuple with updated histories and scores (history1, history2, score1, score2) '''

RELEASE = 0 # (R) when both players collude
TREAT = 100 # (T) when you betray your partner
SEVERE_PUNISHMENT = -500 # (S) when your partner betrays you
PUNISHMENT = -250 # (P) when both players betray each other
# Keep T > R > P > S to be a Prisoner's Dilemma
# Keep 2R > T + S to be an Iterative Prisoner's Dilemma

#Get the two players' actions and remember them.
action1 = get_action(player1, history1, history2, score1, score2)
action2 = get_action(player2, history2, history1, score2, score1)
if type(action1) != str:
    action1=' '
if type(action2) != str:
    action2=' '
#Append the actions to the previous histories, to return
new_history1 = history1 + action1
new_history2 = history2 + action2

#Change scores based upon player actions
if action1 not in ('c','b') or action2 not in ('c','b'):
# Do nothing if someone's code returns an improper action
    new_score1 = score1
    new_score2 = score2
    
else: 
#Both players' code provided proper actions
    if action1 == 'c':
        if action2 == 'c':
            # both players collude; get reward
            new_score1 = score1 + RELEASE
            new_score2 = score2 + RELEASE
        else:
            # players 1,2 collude, betray; get sucker, tempation
            new_score1 = score1 + SEVERE_PUNISHMENT
            new_score2 = score2 + TREAT
    else:
        if action2 == 'c':
            # players 1,2 betray, collude; get tempation, sucker
            new_score1 = score1 + TREAT
            new_score2 = score2 + SEVERE_PUNISHMENT                       
        else:
            # both players betray; get punishment   
            new_score1 = score1 + PUNISHMENT
            new_score2 = score2 + PUNISHMENT
                
#send back the updated histories and scores
return (new_history1, new_history2, new_score1, new_score2)
def play_iterative_rounds(player1, player2): ''' Plays a random number of rounds (between 100 and 200 rounds) of the iterative prisoners' dilemma between two strategies. identified in the parameters as integers. Returns 4-tuple, for example ('cc', 'bb', -200, 600) but with much longer strings ''' number_of_rounds = random.randint(100,200) moves1 = '' moves2 = '' score1 = 0 score2 = 0 for round in range(number_of_rounds): moves1, moves2, score1, score2 = 
play_round(player1, player2, moves1, moves2, score1, score2) return (moves1, moves2, score1, score2)

def get_action(player, history, opponent_history, score, opponent_score, getting_team_name=False): '''Gets the strategy for the player, given their own history and that of their opponent, as well as the current scores within this pairing. The parameters history and opponenet history are strings with one letter per round that has been played so far: either an 'c' for collude or a 'b' for betray. The function should return one character, 'c' or 'b'. The history strings have the first round between these two players as the first character and the most recent round as the last character.'''

######
######
#
# This example player always colludes
if player == 0:
    if getting_team_name:
        return 'loyal'
    else:
        return 'c'


    
        
            
                
                        
######
######
#
#This example player is silent at first and then 
#only betrays if they were a sucker last round.
      
elif player == 1:
    if getting_team_name:
        return 'loyal vengeful'
    else:
        if len(opponent_history)==0: 
            return 'c'
        elif history[-1]=='c' and opponent_history[-1]=='b':
            return 'b' 
        else:
            return 'c' 








######
######
#   
#This example player is silent at first and then 
#only betrays if they were a sucker last round.
elif player == 2:
    if getting_team_name:
        return 'loyal vengeful'
    else:
        if len(opponent_history)==0: #It's the first round: colluide 
            return 'c'
        elif history[-1]=='c' and opponent_history[-1]=='b':
            return 'b' # betray if they were severely punished last time
        else:
            return 'c' #otherwise collude








# Now here are the non example players.
 each team can edit one section of code








######
######
#
elif player == 3:
    if getting_team_name:
        return 'loyal vengeful'
    else:
        # use history, opponent_history, score, opponent_score
        # to compute your strategy
        if len(opponent_history)==0: #It's the first round: collude
            return 'c'
        elif history[-1]=='c' and opponent_history[-1]=='b':
            return 'b' # betray is they were severely punished last time
        else:
            return 'c' #otherwise collude











######
######
#
elif player == 4:
    if getting_team_name:
        return 'betray every 3rd round'
    else:
        # use history, opponent_history, score, opponent_score
        # to compute your strategy
        size = len(history)
        if(size%3==0): #the number of rounds played is a multiple of 3
            return 'c'
        else:
            return 'b'











######
######        
#
elif player == 9:
    if player == 0:
    if getting_team_name:
        return 'betray'
    else:
        return 'b'








######
######        
#
elif player == 6:
    if getting_team_name:
        return 'loyal vengeful'
    else:
        # use history, opponent_history, score, opponent_score
        # to compute your strategy
        if len(opponent_history)==0: #It's the first round: collude
            return 'c'
        elif history[-1]=='c' and opponent_history[-1]=='b':
            return 'b' # betray is they were severely punished last time
        else:
            return 'c' #otherwise collude




######
######        
#
elif player == 7:
    if getting_team_name:
        return 'loyal vengeful'
    else:
          if len(opponent_history)==0: #It's the first round: collude
            return 'c'
        elif history[-1]=='c' and opponent_history[-1]=='b':
            return 'b' # betray is they were severely punished last time
        elif history[-1]=='b' and opponent_history[-1]=='b'
            if random.random()<.33 
                 return 'c'
            else:
                 return 'b'
         elif history[-1]=='c' and opponent_history[-1]=='c'
            if random.random()<.33 
                 return 'b'
            else:
                 return 'c'
         elif history [-1]=='b' and opponent history[-1]=='c'
            return 'c'









######
######        
#
elif player == 8:
    if getting_team_name:
        #if there was a previous round just like 
        return 'loyal vengeful with permanent second impression'
    else:
        # use history, opponent_history, score, opponent_score
        # to compute your strategy      
        if len(opponent_history)==0: #It's the first round: collude
            return 'c'
        else:
            # if there was a previous round just like the last one,
            # do whatever they did in the round that followed it
            recent_round_opponent = opponent_history[-1]
            recent_round_me = history[-1]
                        
            #go through rounds before that one
            for round in range(len(history)-1):
                prior_round_opponent = opponent_history[round]
                prior_round_me = history[round]
                #if one matches
                if (prior_round_me == recent_round_me) and \
                        (prior_round_opponent == recent_round_opponent):
                    return opponent_history[round]
            # no match found
            if history[-1]=='c' and opponent_history[-1]=='b':
                return 'b' # betray is they were severely punished last time
            else:
                return 'c' #otherwise collude
                #I hope this works I'm scared I messed it up.












######
######
#
elif player == 9:
    if getting_team_name:
        return 'loyal vengeful'
    else:
        # use history, opponent_history, score, opponent_score
        # to compute your strategy
        if len(opponent_history)==0: #It's the first round: collude
            return 'c'
        elif history[-1]=='c' and opponent_history[-1]=='b':
            return 'b' # betray is they were severely punished last time
        else:
            return 'c' #otherwise collude










######
######
#
elif player == 10:
    if getting_team_name:
        return 'loyal vengeful'
    else:
        # use history, opponent_history, score, opponent_score
        # to compute your strategy
        if len(opponent_history)==0: #It's the first round: collude
            return 'c'
        elif history[-1]=='c' and opponent_history[-1]=='b':
            return 'b' # betray is they were severely punished last time
        else:
            return 'c' #otherwise collude









######
######
#
elif player == 11:
    if getting_team_name:
        return 'loyal vengeful'
    else:
        # use history, opponent_history, score, opponent_score
        # to compute your strategy
        if len(opponent_history)==0: #It's the first round: collude
            return 'c'
        elif history[-1]=='c' and opponent_history[-1]=='b':
            return 'b' # betray is they were severely punished last time
        else:
            return 'c' #otherwise collude










######
######
#
elif player == 12:
    if getting_team_name:
        return 'loyal vengeful'
    else:
        # use history, opponent_history, score, opponent_score
        # to compute your strategy
        if len(opponent_history)==0: #It's the first round: collude
            return 'c'
        elif history[-1]=='c' and opponent_history[-1]=='b':
            return 'b' # betray is they were severely punished last time
        else:
            return 'c' #otherwise collude




######
######
#
elif player == 13:
    if getting_team_name:
        return 'loyal vengeful'
    else:
        if len(opponent_history)==0: #It's the first round: collude
            return 'c'
        elif history[-1]=='c' and opponent_history[-1]=='b':
            return 'b' # betray is they were severely punished last time
        else:
            return 'c' #otherwise collude









######
######
#
elif player == 14:
    if getting_team_name:
        return 'loyal vengeful occasionally greedy'
    else:
        if len(opponent_history)==0: #It's the first round: collude
            return 'c'
        elif history[-1]=='c' and opponent_history[-1]=='b':
            return 'b' # betray is they were severely punished last time
        else:
            if random.random()<0.1: #10% of the other rounds
                return 'b'         #betray
            else:
                return 'c'         #otherwise collude







######
######
#
elif player == 15:
    if getting_team_name:
        return 'loyal vengeful'
    else:
        if len(opponent_history)==0: #It's the first round: collude
            return 'c'
        elif history[-1]=='c' and opponent_history[-1]=='b':
            return 'b' # betray is they were severely punished last time
        else:
            return 'c' #otherwise collude









######
######
#
elif player == 16:
    if getting_team_name:
        return 'loyal vengeful'
    else:
        if len(opponent_history)==0: #It's the first round: collude
            return 'c'
        elif history[-1]=='c' and opponent_history[-1]=='b':
            return 'b' # betray is they were severely punished last time
        else:
            return 'c' #otherwise collude









######
######
#
elif player == 17:
    if getting_team_name:
        return 'loyal vengeful'
    else:
        if len(opponent_history)==0: #It's the first round: collude
            return 'c'
        elif history[-1]=='c' and opponent_history[-1]=='b':
            return 'b' # betray is they were severely punished last time
        else:
            return 'c' #otherwise collude









######
######
#
elif player == 18:
    if getting_team_name:
        return 'loyal vengeful'
    else:
        if len(opponent_history)==0: #It's the first round: collude
            return 'c'
        elif history[-1]=='c' and opponent_history[-1]=='b':
            return 'b' # betray is they were severely punished last time
        else:
            return 'c' #otherwise collude









######
######
#
elif player == 19:
    if getting_team_name:
        return 'loyal vengeful'
    else:
        if len(opponent_history)==0: #It's the first round: collude
            return 'c'
        elif history[-1]=='c' and opponent_history[-1]=='b':
            return 'b' # betray is they were severely punished last time
        else:
            return 'c' #otherwise collude
def play_tournament(num_players): #create a list of zeros, one per player scores = [] for i in range(num_players): scores += [0]

''' Get the team name from each team algorithm'''
#create a list of the right length
team_names = range(num_players)
for player in range(num_players):
    team_names[player] = get_action(player,'','',0,0,getting_team_name=True)
         
# each element will become a column for each player
# range is just to get list of correct size
result_table=range(num_players)     
moves_table=range(num_players) 


for player1 in range(num_players):  
    # create the column for each player
    # range just to get list of correct size
    result_table[player1]=range(num_players) 
    result_table[player1][player1]=0 # initialize unused diagonal to 0
    moves_table[player1]=range(num_players)
    # play a game between with every other player of lower number
    for player2 in range(player1):
        moves1, moves2, score1, score2 = \
            play_iterative_rounds(player1, player2)
        
        rounds = len(moves1)
        score1_per_round = score1/rounds 
        score2_per_round = score2/rounds
        
        result_table[player1][player2]=score1_per_round
        result_table[player2][player1]=score2_per_round
        
        moves_table[player1][player2] = moves1
        moves_table[player2][player1] = moves2
        
        #accumulate the results for the two players
        scores[player1] += score1*1.0/len(moves1)#ends up same as column sum
        scores[player2] += score2*1.0/len(moves2)#ends up same as column sum
 
'''report round-level results in a data file'''
use_datafile=True
if use_datafile:
    # use the same directory as the python script
    import os.path              
    directory = os.path.dirname(os.path.abspath(__file__))  
    
    #name the file tournament.txt
    filename = os.path.join(directory, 'tournament.txt')
    #create the file for the round-by-round results
    results = open(filename,'w')
    for player1 in range(num_players):
        for player2 in range(player1):
            # store the results in the file
            #title by team numbers
            results.write('team ' + str(player1) + 
                          ' vs. ' + 'team ' + str(player2) +'\n')
            #title by player-on-player average score
            results.write(str(result_table[player1][player2]) + 
                          ' vs. ' + str(result_table[player2][player1])+'\n')
            #title by team names
            results.write(team_names[player1] + 
                         ' vs. ' + team_names[player2] + '\n')
            #show the moves, aligned vertically
            results.write(moves_table[player1][player2] +'\n')
            results.write(moves_table[player2][player1] +'\n')
            #blank line between each pair's results
            results.write('\n')
        
    #at the bottom repeat the output that was sent to the screen
    #print a title for the table
    results.write('\n\n\n\tEach column shows score earned per round against each other player.\n\n\n')
    #print header line
    results.write('\t') #skip 1st column
    for player1 in range(num_players):
        results.write('P'+str(player1)+'\t') # label each additional column
    results.write('\n')
    
    #print each player's scores
    for player2 in range(num_players):
        results.write('P'+str(player2)+'\t') #label the player's row
        for player1 in range(num_players):
            #print score against each other player
            results.write(str(result_table[player1][player2])+'\t') 
        results.write('\n')
    results.write('Total:\t')
    for player1 in range(num_players):
        results.write(str(int(scores[player1]))+'\t')
    results.write('\n\n\n Average per round, with team strategy names:\n\n')       

    #print team ids, total scores, and names
    for player in range(num_players):
        results.write('player ' + str(player) + ': ' + \
                str(int(scores[player])/num_players) + ' points: '+\
                team_names[player]+'\n')
                
                
    #append the file showing algorithms
    results.write('\n\n' + '-'*79 + '\n' + \
                'Here is the code that produced this data:\n\n')
    this_code_file = open(__file__, 'r')
    for line in this_code_file:
        results.write(line)
            
'''report the results on screen'''        
#print a title for the table
print('\n\n\tEach column shows score earned per round against each other player.\n\n')

#print header line
print('\t', end='') #skip 1st column
for player1 in range(num_players):
    print('P',player1, end='\t') # label each additional column
print()

#print each player's scores
for player2 in range(num_players):
    print('P',player2, end='\t') #label the player's row
    for player1 in range(num_players):
        #print score against each other player
        print(result_table[player1][player2], end='\t') 
    print()
#print row of total scores
print('Total:\t',end='')
for player1 in range(num_players):
    print(str(int(scores[player1])),end='\t')

print('\n\n\n Average per round, with team strategy names:\n\n')
#print team ids, total scores, and names
for player in range(num_players):
    print('player ' + str(player) , ': ' , 
           str(int(scores[player])/num_players) , ' points: ',
           team_names[player])
