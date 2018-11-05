
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


