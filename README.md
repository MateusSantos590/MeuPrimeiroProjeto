# MeuPrimeiroProjeto
# Projeto Python - Mercado - desenvolvimento
 Primeiro Repositório do Git e GitHub




! Explicar Detalhes sobre o Código
#! Desenvolver Banco de Dados

 
#! O CÓDIGO PRECISA DE ALGUNS AJUSTES BÁSICOS


#? Lógica de Programação: 
#* 1- Primeiro o Cliente Precisa Pegar os Itens desejados e depois Passar no Caixa com as Compras
#* 2- Segundo Olhar o Valor Total da Compra
#* 3- Pegar Cartão/Dinheiro 
#* 4- Colocar sua Senha (Caso for passar no cartão)
#* Entre Outras Funções

# instalando Bibliotecas
import time

senha_cartao_correta = 1234
tentativas = 0

print('--' * 15)
print('Bem-Vindo ao Mercado!')
print('--' * 15)

itens_disponiveis = ['Arroz', 'Feijão', 'Cartela de Ovo', 'Biscoito', 'Biscoito Recheado Sabor Morango', 'Biscoito Recheado de Chocolate', 'Biscoito Recheado Sabor Creme', 'Achocolatado',
                    'Danone', 'Farinha', 'Bolo de Chocolate', 'Bolo de Milho', 'Bolo de Morango']
precos_itens = [22.99, 29.99, 13.99, 3.99, 2.99, 3.99, 4.99, 10.99, 16.99, 9.99, 42.99, 45.99, 39.99, 46.99]

print('--' * 15)

combinando = dict(zip(itens_disponiveis, precos_itens))

carrinho = []

while True:
    print('--' * 15)
    print(f'Itens disponíveis: {combinando}')
    print('--' * 15)
    item = input('Qual item você gostaria de adicionar ao carrinho? (Digite "sair" para finalizar a compra): ').capitalize()
    if item == 'Sair':
        break
    #* Se o item estiver disponível (ou seja, se estiver no dicionário combinando), o preço do item será adicionado ao carrinho.
    elif item in combinando:
        carrinho.append(combinando[item])
    else:
        print('Item não disponível.')

    total = sum(carrinho)
    print('Calculando o total das compras...')
    time.sleep(2)
    print(f'O total da sua compra é: R${total:.2f}')

    print(f'Forma de Pagamento Cartão de Débito ou Crédito')
    cliente = str(input('A forma de Pagamento Será... ')).capitalize().strip()

    if cliente in ['Debito', 'Débito']:
        print('Pode inserir o Cartão...')
        time.sleep(1)
        print('Digite a Senha')
        senha_cartao = int(input('Senha do Cartão: '))          
        if senha_cartao == senha_cartao_correta:
            continue
        else:
            tentativas += 1
            if tentativas >= 3:
                print('Cartão Bloqueado')
                print('Compra Suspensa...')
                break
            else:
                print('Senha está incorreta!')
                print('Você tem Três tentativas; para o cartão bloquear')
    elif cliente in ['Credito', 'Crédito']:
        parcelar_compras = str(input('Deseja Parcela? ')).capitalize().strip()
        if parcelar_compras == 'Sim':
            print('--' * 15)
            print('AVISO: Todas as Compras com parcelamento ACIMA de 4x, irá pagar R$65 de juros por mês')
            print('--' * 15)
            quantas_vezes = int(input('Quantas Vezes: '))
            if quantas_vezes >= 4:
                total += 65 / quantas_vezes
                print(f'Total: {total:.2f}')
            else:
                print(f'Total: {total:.2f}')
            print('Pode inserir o Cartão...')
            time.sleep(1)
            print('Digite a Senha')
            senha_cartao = int(input('Senha do Cartão: '))          
            if senha_cartao == senha_cartao_correta:
                continue
            else:
                tentativas += 1
                if tentativas >= 3:
                    print('Cartão Bloqueado')
                    print('Compra Suspensa...')
                    break
                else:
                    print('Senha está incorreta!')
                    print('Você tem Três tentativas; para o cartão bloquear')
print('FIM DO PROGRAMA')

