print("=== Calculadora de Probabilidade ===")

casas_favoráveis = int(input("Digite o número de casas favoráveis: "))
casas_possíveis = int(input("Digite o número de casas possíveis: "))

if casas_possíveis <= 0:
    print("O número de casas possíveis deve ser maior que zero.")
elif casas_favoráveis < 0 or casas_favoráveis > casas_possíveis:
    print("Os casas favoráveis devem estar entre 0 e os casos possíveis.")
else:
    probabilidade = casas_favoráveis / casas_possíveis
    porcentagem = probabilidade * 100

    print("A probabilidade é:", probabilidade)
    print("A probabilidade em porcentagem é:", porcentagem, "%")
