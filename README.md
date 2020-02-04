
import pandas as pd

df = pd.read_excel (r'C:\Users\phili\stock_search\stock_locations.xlsx')
pd.set_option('display.max_columns', 4)
pd.set_option('display.max_rows', 4096)



def search(data=df):
    
    
        
    decide_search = input("Seacrh by PART or DESCRIPTION?\nEnter 'P' or 'D'\n>>>").upper()
        
    #asked the user which type of search they want to perform    
       
    if decide_search == 'P':
        
            
            type_part = input('Enter a part number: ') 
            print("Type 'E' to exit")
   #part numbers often contain a str + int        
   #therefore, interger only part numbers had to be identified to avoid Error        
            
            if type_part.isdigit():
                
                user_data = int(type_part)
                print(df[df.Item == user_data])
                    
            elif not type_part.isdigit():
                user_data = str(type_part).upper()
                print(df[df.Item == user_data])
                    
            elif type_part == 'E':
                print('Search ended')
                
            else:
                user_data not in df['Item']
                print('Part number not in database')
                
   #search via description based on keywords        
       
    if decide_search == 'D':
            
       type_des = input(str('Enter a description: ')).upper()
            
       print(df[df['Item Description'].str.contains(type_des)])
    
    if decide_search != 'P' or decide_search != 'D':
        print('Invalid Selection')
        
