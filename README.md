

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
    
