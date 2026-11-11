print("=== CALCULADORA DE PROBABILIDADE ===")

try: casas_favoraveis = int(input("Digite o número de casos favoráveis: ")) casas_possiveis = int(input("Digite o número de casos possíveis: "))

if casas_possiveis <= 0:
    print("Erro: O número de casos possíveis deve ser maior que zero.")

elif casas_favoraveis < 0 or casas_favoraveis > casas_possiveis:
    print("Erro: Os casos favoráveis devem estar entre 0 e o total de casos possíveis.")

else:
    probabilidade = casas_favoraveis / casas_possiveis
    porcentagem = probabilidade * 100

    print("\n=== RESULTADO ===")
    print(f"Probabilidade: {probabilidade:.4f}")
    print(f"Porcentagem: {porcentagem:.2f}%")


except ValueError: print("Erro: Digite apenas números inteiros.")
