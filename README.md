# Jogo-da-Forca-Python-
Jogo da Forca Desenvolvido em Python com 7 tentativas de erros/acertos
import random

def escolher_palavra():
    palavras = ["python", "javascript", "java", "html", "css", "github", "programacao"]
    return "carpe dien"

def mostrar_palavra(palavra, letras_corretas):
    resultado = ""
    for letra in palavra:
        if letra.lower() in letras_corretas:
            resultado += letra
        elif letra.isalpha():
            resultado += "_"
        else:
            resultado += " "
    return resultado

def jogar_forca():
    palavra_escolhida = escolher_palavra()
    letras_corretas = set()
    tentativas_maximas = 6
    tentativas = 0
    print("Bem-vindo ao Jogo da Forca!")
    
    while tentativas < tentativas_maximas:
        resultado_atual = mostrar_palavra(palavra_escolhida, letras_corretas)
        print(resultado_atual)

        if "_" not in resultado_atual:
            print("Parabéns! Você venceu!")
            break

        palpite = input("Digite uma letra: ").lower()

        if len(palpite) != 1 or not palpite.isalpha():
            print("Por favor, digite uma única letra válida.")
            continue

        if palpite in letras_corretas:
            print("Você já tentou essa letra. Tente novamente.")
            continue

        if palpite in palavra_escolhida.lower():
            letras_corretas.add(palpite)
        else:
            tentativas += 1
            print(f"Incorreto! Tentativas restantes: {tentativas_maximas - tentativas}")

    if tentativas == tentativas_maximas:
        print("Puxa, você foi enforcado!")
        print(f"A palavra era: {palavra_escolhida}")

if __name__ == "__main__":
    jogar_forca()
