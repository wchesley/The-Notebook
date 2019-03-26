# Otree Project:

Assisting Dr. Hoffman and Dr. Barthrel in creating and improving economics and business related games based on the otree framework. 

#TODO: 

 -KanBan board-
* improved admin page
    * admin graph page. 
* Bot AI
* Remove multiple pages in Bank_run_new and og Bank_run, (only % is changing per round ref: templates)
* Remove multiple class calls in bank_run views.py, ties into above item
* verify battle_of_the_sexes => can we reach all possible choices with that if else block?
* beauty_class models.py, tie is instatiated and intialized to false twice. 

## Loose Notes: 
    dynamic sessions only when not created in demo mode, have to set up session each time. 
    certain variables are best set as constants.
    currently have an error: `TypeError: '>' not supported between instances of 'decimal.Decimal' and 'function' django`
    question is, how to return data from settings.py as a primative data type rather than a function (explicit casting won't work)

