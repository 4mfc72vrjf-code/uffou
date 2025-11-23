import random

def jeu(mini, maxi, essais):
    b = random.randint(mini, maxi)

    print(f"\nJ'ai choisi un nombre entre {mini} et {maxi}.")
    print(f"Tu as {essais} essais.")

    nb_essais = essais

    while essais > 0:
        n = int(input("➡️  Entre un nombre : "))

        if n == b:
            print("\n🎉 Bravo ! C'est le bon nombre !")
            print("Tu as réussi en", nb_essais - essais + 1, "essai(s).")
            return True

        elif n < b:
            print("⬆️ Trop petit.")
        else:
            print("⬇️ Trop grand.")

        essais -= 1

    print("\n❌ Dommage, tu as perdu ! Le nombre était", b)
    return False


def menu():
    print("\n===== DEVINE LE NOMBRE =====")
    print("1. Jouer")
    print("2. Règles")
    print("3. Quitter")
    return input("Choix : ")


def regles():
    print("\n📘 RÈGLES DU JEU :")
    print("- L'ordinateur choisit un nombre au hasard.")
    print("- Tu dois le deviner en quelques essais.")
    print("- L'ordi te dit si c'est plus haut ou plus bas.\n")


def choisir_difficulte():
    print("\nChoisis une difficulté :")
    print("1. Facile (1-50, 10 essais)")
    print("2. Normal (1-100, 5 essais)")
    print("3. Difficile (1-500, 7 essais)")

    choix = input("Choix : ")

    if choix == "1":
        return 1, 50, 10
    elif choix == "2":
        return 1, 100, 5
    else:
        return 1, 500, 7


# --- PROGRAMME PRINCIPAL ---

victoires = 0
defaites = 0

while True:
    choix = menu()

    if choix == "1":
        mini, maxi, essais = choisir_difficulte()
        if jeu(mini, maxi, essais):
            victoires += 1
        else:
            defaites += 1

        print(f"\n⭐ Score : {victoires} victoire(s), {defaites} défaite(s)")

        rejouer = input("\nTu veux rejouer ? (o/n) : ")
        if rejouer != "o":
            break

    elif choix == "2":
        regles()

    elif choix == "3":
        print("\nMerci d'avoir joué ! 👋")
        break

    else:
        print("Choix invalide.")
