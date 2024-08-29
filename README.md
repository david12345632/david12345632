
import random

# Liste med geografiske spørgsmål og svar
questions = [
    {"question": "Hvad er hovedstaden i Frankrig?", "answer": "Paris"},
    {"question": "Hvilket land har flest øer?", "answer": "Sverige"},
    {"question": "Hvilket land er det største i verden?", "answer": "Rusland"},
    {"question": "Hvilken flod er den længste i verden?", "answer": "Nilen"},
    {"question": "Hvilken ørken er den største i verden?", "answer": "Sahara"},
    {"question": "Hvad er hovedstaden i Japan?", "answer": "Tokyo"},
    {"question": "Hvilken ø er den største i verden?", "answer": "Grønland"},
    {"question": "Hvad er det højeste bjerg i verden?", "answer": "Mount Everest"},
    {"question": "Hvad er hovedstaden i Australien?", "answer": "Canberra"},
    {"question": "Hvilken sø er den dybeste i verden?", "answer": "Baikalsøen"}
]

def ask_question(player):
    """Stil et spørgsmål til spilleren og returnér om det var korrekt."""
    question = random.choice(questions)
    print(f"{player}, {question['question']}")
    answer = input("Svar: ").strip()

    if answer.lower() == question["answer"].lower():
        print("Korrekt!")
        return True
    else:
        print(f"Forkert! Det rigtige svar er {question['answer']}.")
        return False

def play_game():
    """Spil et rundebaseret geografispil."""
    print("Velkommen til Geografisk Rejse!")
    players = input("Indtast spillernavne, adskilt af kommaer: ").split(',')
    players = [player.strip() for player in players]
    scores = {player: 0 for player in players}

    rounds = int(input("Hvor mange runder vil I spille? "))

    for i in range(rounds):
        print(f"\nRunde {i+1}/{rounds}")
        for player in players:
            if ask_question(player):
                scores[player] += 1

    print("\nSpillet er slut! Her er slutresultaterne:")
    for player, score in scores.items():
        print(f"{player}: {score} point")

    winner = max(scores, key=scores.get)
    print(f"\nVinderen er {winner} med {scores[winner]} point! Tillykke!")

if __name__ == "__main__":
    play_game()
