''' 
PrisonerDilemma.py allows hard-coding different strategies
for the Iterative Prisoners Dilemma, the canonical game of game-theory.
Each strategy plays 100 to 200 rounds against each other strategy.
The results of all previous rounds within a 100-200 round stretch are known
to both players. 

play_tournament() executes the tournament and stores output in tournament.txt

Players should each code their strategies in their assigned section of code.

Aggregated results are stored in tournament.txt

Unpublished work (c)2013 Project Lead The Way
CSE Project 1.3.5 Collaborating on a Project
Draft, Do Not Distribute
Version 8/23/2013 
'''

import random
def play_round(player1, player2, history1, history2, score1, score2):
    '''
    Calls the get_action() function which will get the characters
    'c' or 'b' for collude or betray for each player.
    The history is provided in a string, e.g. 'ccb' indicates the player
    colluded in the first two rounds and betrayed in the most recent round.
    Returns a 4-tuple with updated histories and scores
    (history1, history2, score1, score2)
    '''
    
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
   
def play_iterative_rounds(player1, player2):
    '''
    Plays a random number of rounds (between 100 and 200 rounds) 
    of the iterative prisoners' dilemma between two strategies.
    identified in the parameters as integers.
    Returns 4-tuple, for example ('cc', 'bb', -200, 600) 
    but with much longer strings 
    '''
    number_of_rounds = random.randint(100,200)
    moves1 = ''
    moves2 = ''
    score1 = 0
    score2 = 0
    for round in range(number_of_rounds):
        moves1, moves2, score1, score2 = \
            play_round(player1, player2, moves1, moves2, score1, score2)
    return (moves1, moves2, score1, score2)

def get_action(player, history, opponent_history, score, opponent_score, getting_team_name=False):
    '''Gets the strategy for the player, given their own history and that of
    their opponent, as well as the current scores within this pairing.
    The parameters history and opponenet history are strings with one letter
    per round that has been played so far: either an 'c' for collude or a 'b' for 
    betray. The function should return one character, 'c' or 'b'. 
    The history strings have the first round between these two players 
    as the first character and the most recent round as the last character.'''
      
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
    #This example player always betrays.      
    elif player == 1:
        if getting_team_name:
            return 'backstabber'
        else:
            return 'b'








    ######
    ######
    #   
    #This example player is silent at first and then 
    #only betrays if they were a sucker last round.
    elif player == 2:
        if getting_team_name:
            return 'loyal vengeful'
        else:
            if len(opponent_history)==0: #It's the first round: collude
                return 'c'
            elif history[-1]=='c' and opponent_history[-1]=='b':
                return 'b' # betray if they were severely punished last time
            else:
                return 'c' #otherwise collude


    
    
    
    
    # EACH STUDENT TEAM CAN CHANGE ONE OF THESE elif SEGMENTS OF CODE.










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
    
