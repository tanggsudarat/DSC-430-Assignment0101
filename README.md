# Grading Logic




# Name: Sudarat Namchaiya
# "I have not given or recieved any unauthorized assistance on this assignment"


### 4 Helper fuunctions ###
def correctFile():
    '''
    This function returns answer (Y/N) if the submission file is correct
    '''
    return input("Did the student submit a single uncompressed file?: ")

def includesName():
    '''
    This function returns answer (Y/N) if student includes  their name and date
    '''
    return input("Did the student include their name and date?: ") 

def honorStatement():
    '''
    This function returns answer (Y/N) if student includes  the honor statement
    '''
    return input("Did the student put the honor statement on the assignment?: ")

def submitVideo():
    '''
    This function returns answer (Y/N) if student submits 3 mins video
    '''
    return input("Did the student submit and 3 mins Youtube Video presenting the code and answering questions?: ")


def computeGrade():
    '''this function asks the user a series of questions based on grading logic for this class and 
    returns students total score out of 40 '''
    
    #Chek if meet all conditions of the helper functions
    print ('Please answer the below questions ( Y or N)')
    if correctFile() != 'Y':    
        return 0                    #return 0 if does not meet the condition
    if includesName() != 'Y':
        return 0
    if honorStatement() != 'Y':
        return 0
    if submitVideo() != 'Y':
        return 0

    print('Congratulations!! student meets all above condition')
    print('Up to ten (0-10), please score their work based on')         
    
    # input scores in each criteria
    score1 = int(input("1.How well the correctness of code meets the given specifications: "))  
    score2 = int(input("2.The elegance of code such as Data structure selection, algorithm efficiency, etc: "))
    score3 = int(input("3.The code hygiene such as white space, docstrings, etc: "))
    score4 = int(input("4.Quality of discussion in Youtube Video: "))

    res = score1 + score2 + score3 + score4                             # 1st compute the summary of all scores
    
    Late = input('Did the student submit the assignment late?(Y/N): ')  # Asking if the submission is late

    if Late == 'Y':
        LateHR = input("How many hours that this assignment was late for the submission?: ")
        Latelost = 0.01*40*int(LateHR)        # compute the late lost(loss 1% of total possible per hour)
        res -= Latelost                       # compute A new total 

        if res < 0:                 # If a new total that substract Latelost is lower than 0
            return 0                # return 0 because score cant be negative
        else: 
            return float(res)       # return a new total
    else:                           # if it is not late 
        return res                  # return the 1st compute of total scores


score = computeGrade()
result = 'Your score is'+' '+ str(score)
print (result)
