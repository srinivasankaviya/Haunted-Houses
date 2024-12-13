# Haunted-Houses
import random

def display_ghost():
    print("""
         .-.
        (o o)    
        | O |    
        |   |    
       '-----'
    """)
    print("A ghost appears! You feel a chill in the air.")

def math_challenge():
    num1 = random.randint(1, 10)
    num2 = random.randint(1, 10)
    answer = num1 + num2
    user_answer = int(input(f"What is {num1} + {num2}? "))
    return user_answer == answer
def choose_potion():
    print("You see three potions on the kitchen table:")
    print("1. Red Potion")
    print("2. Blue Potion")
    print("3. Green Potion")
    choice = input("Which potion do you choose? (1/2/3) ")
   
    if choice == '1':
        print("You feel a warm glow. it gives a temporary invisible power.!")
    elif choice == '2':
        print("You feel a chill.the secret passage will revealed !")
    elif choice == '3':
        print("You feel dizzy. now you can communicate with spirits.")
    else:
        print("Invalid choice! You stand there confused.")

def main():
    rooms = {
        'bedroom': display_ghost,
        'kitchen': choose_potion,
        'library': lambda: print("You find a secret passage to the kitchen!"),
        'living room': math_challenge
    }

    print("Welcome to the Haunted House!")
    while True:
        room = input("Which room do you want to enter? (bedroom/kitchen/library/living room/exit): ").lower()
        if room == 'exit':
            print("Thanks for playing! Goodbye!")
            break
        elif room in rooms:
            print(f"You enter the {room}.")
            if room == 'living room':
                if not math_challenge():
                    print("Wrong answer! You lose.")
                    break
            else:
                rooms[room]()
        else:
            print("That's not a valid room!")

if __name__ == "__main__":
    main()
