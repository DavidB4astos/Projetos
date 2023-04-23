menu = '''

Menu de opções


[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair

'''

saldo = 0
limite = 500
extrato = ''
numero_saques = 0
LIMITES_SAQUES = 3

while True:

    opcao = input(menu)

    if opcao == 'd':
        valor = float(input('Digite o valor para depósito: '))

        if valor > 0:
            saldo += valor
            extrato += f'Depósito: {valor:.2f}\n'

        else:
            print('Operação falhou! o valor é invalido')

    elif opcao == 's':
        valor = float(input('Digite o valor para saque: '))

        exedeu_saldo = valor > saldo

        exedeu_limite = valor > limite

        exedeu_saques = numero_saques >= LIMITES_SAQUES

        if exedeu_saldo:
            print('Operação falhou! Saldo insuficiente')

        elif exedeu_limite:
            print('Operação falhou! Limite excedido')

        elif exedeu_saques:
            print('Operação falhou! Limite de saques excedido')

        elif valor > 0:
            saldo -= valor
            extrato += f'Saque: {valor:.2f}\n'
            numero_saques += 1

        else:
            print('Operação falhou! o valor é invalido')

    elif opcao == 'e':
        print('\n============= EXTRATO =============')
        print('Não foram realizadas operações' if not extrato else extrato)
        print(f'\nSaldo: R$ {saldo:.2f}')
        print('======================================')

    elif opcao == 'q':
        break

    else:
        print('Operação inválida! Digite uma opção válida')
