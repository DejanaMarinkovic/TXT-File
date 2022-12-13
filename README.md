# TXT-File
import re

# Otvaram ulaznu i izlaznu datoteku
with open('C:\Users\Admin\PycharmProjects\pythonProject\izrazi.txt', 'r') as f:
    with open ( "C:\Users\Admin\PycharmProjects\pythonProject\izlaz.txt", 'r+' ) as file:

        # Citam ulaznu datoteku
        izrazi = f.read()

        # Definisem recnik operatora i njihove odgovarajuce funkcije
        operators = {
            '+': lambda operand1, operand2: operand1 + operand2,
            '-': lambda operand1, operand2: operand1 - operand2,
            '': lambda operand1, operand2: operand1 operand2,
            '/': lambda operand1, operand2: operand1 / operand2,
        }

        # Prolazim kroz svaki izraz u ulazu
        for izraz in izrazi.split ( '\n' ):
            # Koristim regularni izraz da bi izdvjila operande i operatore
            match = re.search(r'(\d+)([+-/*])(\d+)',izraz)

            # Proveravam da li је ulazni izraz ispravan
            if match:
                # Izdvajam operande i operatore
                operand1 = int(match.group(1))
                operator = match.group(2)
                operand2 = int(match.group(3))

                # Primenjujem operator na operande
                rezultat = operators[operator](operand1, operand2)

                # Format rezultata je string
                konacanrazultat = (f"{operand1}{operator}{operand2}={rezultat}\n")

                # Upisujem rezultat u novi fajl
                file.write(konacanrazultat)
