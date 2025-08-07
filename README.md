saldo = 0
limite = 500
extrato = ""
saques_realizados = 0
limite_saques = 3

while True:
    print("\n====== MENU ======")
    print("1 - Depositar")
    print("2 - Sacar")
    print("3 - Ver Extrato")
    print("0 - Sair")
    print("==================")

    opcao = input("Escolha uma opção: ")

    if opcao == "1":
        valor = float(input("Digite o valor do depósito: "))

        if valor > 0:
            saldo += valor
            extrato += f"Depósito: R$ {valor:.2f}\n"
            print("Depósito feito com sucesso!")
        else:
            print("Valor inválido! Digite um valor positivo.")

    elif opcao == "2":
        valor = float(input("Digite o valor do saque: "))

        if valor <= 0:
            print("Valor inválido! Digite um valor maior que zero.")
        elif valor > saldo:
            print("Você não tem saldo suficiente.")
        elif valor > limite:
            print("O valor do saque ultrapassa o limite de R$ 500.00.")
        elif saques_realizados >= limite_saques:
            print("Você atingiu o limite de 3 saques por dia.")
        else:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2f}\n"
            saques_realizados += 1
            print("Saque feito com sucesso!")

    elif opcao == "3":
        print("\n===== EXTRATO =====")
        if extrato == "":
            print("Não foram feitas movimentações.")
        else:
            print(extrato)
        print(f"Saldo atual: R$ {saldo:.2f}")
        print("===================")

    elif opcao == "0":
        print("Saindo do sistema... Até mais!")
        break

    else:
        print("Opção inválida, tente de novo.")
