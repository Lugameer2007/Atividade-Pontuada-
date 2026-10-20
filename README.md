programa
{
	
	funcao inicio()
	{
		real preco, subtotal, desconto, total
		real recebido, troco, parcela 
		real maior_preco
		inteiro quantidade, pagamento, parcelas

		subtotal = 0.0
		desconto = 0.0
		total = 0.0
		recebido = 0.0
		troco = 0.0
		maior_preco = 0.0
		quantidade = 0

		escreva("=== Mercadinho Boa Vizinhanca ===\n")
		escreva("Digite os preços dos produtos.\n")
		escreva("Digite 0 para encerrar os itens.\n\n")

		//Cadastro dos preços 
		enquanto (verdadeiro) 
		{
			escreva("Preço do produto: R$ ")
			leia(preco)

			se (preco == 0)
			{
				pare
			}
			senao
			{
				se (preco < 0)
				{
					escreva("Preço invalido! Digite um valor positivo.\n")
				}
				senao 
				{
					subtotal = subtotal + preco
					quantidade = quantidade + 1

					se (preco > maior_preco)
					{
						maior_preco = preco
					}

					escreva("Produto registrado!\n")
				}
			}
		}
		
		//Verificação de compra vazia 
		se (quantidade == 0)
		{
			escreva("\nNenhuma compra registrada.\n")
		}
		senao
		{
			//Calculo do desconto 
			se (subtotal >= 100.0)
			{
				desconto = subtotal * 0.10
			}

			total = subtotal - desconto

			escreva("\n=== Resumo da Compra ===\n")
			escreva("Quantidade de itens: ", quantidade,  "\n")
			escreva("Maior_preco: R$ ", maior_preco, "\n")
			escreva("Subtotal: R$ ", subtotal, "\n")
			escreva("Desconto: R$ ", desconto, "\n")
			escreva("Total a pagar: R$ ", total, "\n")

			//Escolha a forma de pagamento
			pagamento = 0

			enquanto (pagamento != 1 e pagamento != 2)
			{
				escreva("\n=== Forma de Pagamento ===\n")
				escreva("1 - Dinheiro\n")
				escreva("2 - Cartao\n")
				escreva("Escolha: ")
				leia(pagamento)

				se(pagamento != 1 e pagamento != 2)
				{
					escreva("Opcao invalida! Escolha 1 ou 2.\n")
				}
			}

			//Paagamento em dinheiro
			se (pagamento == 1)
			{
				faca
				{
					escreva("Valor recebido: R$ ")
					leia(recebido)

					se (recebido < total)
					{
						escreva("Valor insuficiente! Digite novamente.\n")
					}
				} enquanto(recebido < total)

				troco = recebido - total 

				escreva("\nPagamento em dinheiro.\n")
				escreva("Valor recebido: R$ ", recebido, "\n")
				escreva("Troco: R$ ", troco, "\n")
			}
			senao
			{
				// Pagamento no cartao
				se (total < 20.0)
                {
                    escreva("\nO cartao nao pode ser utilizado nesta compra.\n")
                    escreva("O valor total nao permite parcela de R$ 20,00.\n")
                    escreva("Escolha o pagamento em dinheiro na proxima tentativa.\n")
                }
                senao
                {
                    parcelas = 0

                    enquanto (parcelas < 1 ou parcelas > 6)
                    {
                        escreva("Numero de parcelas (1 a 6): ")
                        leia(parcelas)

                        se (parcelas < 1 ou parcelas > 6)
                        {
                            escreva("Numero invalido! Digite de 1 a 6.\n")
                        }
                        senao
                        {
                            parcela = total / parcelas

                            se (parcela < 20.0)
                            {
                                escreva("Cada parcela deve ser de pelo menos R$ 20,00.\n")
                                parcelas = 0
                            }
                        }
                    }

                    parcela = total / parcelas

                    escreva("\nPagamento no cartao.\n")
                    escreva("Quantidade de parcelas: ", parcelas, "\n")
                    escreva("Valor de cada parcela: R$ ", parcela, "\n")

                    inteiro contador
                    contador = 1

                    enquanto (contador <= parcelas)
                    {
                        escreva("Parcela ", contador, ": R$ ", parcela, "\n")
                        contador = contador + 1
                    }
			          }
		        }
        }
    }
	}
}
