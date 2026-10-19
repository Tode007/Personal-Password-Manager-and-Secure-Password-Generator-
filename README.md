import random 
import string 

passwords = {}

#Load existing password file

try:
    with open ('passwords.txt', 'r') as file:
        for line in file:
            website, pwd = line.strip().split(':')
            passwords[website]=pwd
except:
    pass
def generate_password():
    chars = string.ascii_letters + string.digits+'!@#$%&'
    password = '' .join(random.choice(chars) for _ in range(6))
    return password

while True:
    print('\n----Personal Password App----')
    print('1.Save Password')
    print('2.View Passwords')
    print('3.Generate Password')
    print('4.Exit')
    
    choice = input('Enter ur choice')
    
    if choice == '1':
        site = input('enter website : ')
        pwd = input('enter ur password: ')
        
        passwords[site] = pwd
        
        with open('passwords.txt', 'a') as file:
            file.write(f'{site}:{pwd}\n')
        print('saved!')
    elif choice == '2':
        if not passwords:
            print('No data')
        else:
            for site, pwd in passwords.items():
                print(site,':',pwd)
    elif choice == '3':
        print("Generate Password", generate_password())
    elif choice =='4':
        print('See you')
        break
    else:
        print('something is invalid')
