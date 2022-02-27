# g-n-rateur-password
import random
from os import system

def header():
    return("""__________                   ___               __________                                                ___
\______   \____    ____   __| _/ ____   _____  \______   \____    ______ _______  _  __ ____ _______  __| _/
 |       _/__  \  /    \ / __ | / __ \ /     \  |     ___/__  \  /  ___//  ___/ \/ \/ // __ \\_  __ \/ __ | 
 |    |   \/ __ \_   |  \ /_/ |(  \_\ )  | |  \ |    |    / __ \_\___ \ \___ \ \     /(  \_\ )|  | \/ /_/ | 
 |____|_  /____  /___|  /____ | \____/|__|_|  / |____|   (____  /____  \____  \ \/\_/  \____/ |__|  \____ | 
        \/     \/     \/     \/             \/                \/     \/     \/                           \/ 
""")

def generate_password():
    system("cls")
    caratacters = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%^&*()_+"
    password = ""
    length = int(input("Entrez la longueur du mot de passe -> "))

    while len(password) < length:
        password += random.choice(caratacters)
    print("Votre mot de passe est : " + password)

    with open("password.txt", "a+") as file:
        file.write(f"{password}\n")
        file.close()

    input("Appuyez sur une touche pour continuer")
    menu()

def list_password():
    system("cls")
    print("liste de mots de passe :\n")

    with open("password.txt", "r+") as file:
        for p in file.readlines():
            print(p)

    input("Appuyez sur une touche pour continuer")
    menu()

def menu():
    print(header())

    print("""
    [1] - Générer un mot de passe
    [2] - Liste de mots de pass
    [3] - Quit
    """)

    choice = input("Entrez votre choix -> ")

    if choice == "1":
        generate_password()
    elif choice == "2":
        list_password()
    elif choice == "3":
        system("cls")
        print("Au revoir")
    else:
        system("cls")
        menu()


if __name__ == "__main__":
    menu()
Copyright (c) 2022 Naxtag
