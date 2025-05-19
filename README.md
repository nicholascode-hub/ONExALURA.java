# ONExALURA.java
este repositório é baseado na trilha de estudos JAVA(Oracle),na qual tenho estudado na plataforma Alura.


/*
 * Programa: Sistema de Gerenciamento de Cartão de Crédito
 * Descrição: Este programa simula um sistema básico de cartão de crédito,
 * permitindo que o usuário defina um limite, registre compras e
 * verifique o saldo disponível.
 */

        Scanner leitura = new Scanner(System.in);
        System.out.println("Digite o limite do cartão: ");
        double limite = leitura.nextDouble();
        CartaoDeCredito cartao = new CartaoDeCredito(limite);

        int sair = 1;
        while(sair != 0) {
            System.out.println("Digite a descrição da compra:");
            String descricao = leitura.next();

            System.out.println("Digite o valor da compra:");
            double valor = leitura.nextDouble();

            Compra compra = new Compra(descricao, valor);
            boolean compraRealizada = cartao.lancaCompra(compra);

            if (compraRealizada) {
                System.out.println("Compra realizada!");
                System.out.println("Digite 0 para sair ou 1 para continuar");
                sair = leitura.nextInt();
            } else {
                System.out.println("Saldo insuficiente!");
                sair = 0;
            }
        }

        System.out.println("***********************");
        System.out.println("COMPRAS REALIZADAS:\n");

        for (Compra c : cartao.getCompras()) {
            System.out.println(c.getDescricao() + " - " +c.getValor());
        }
        System.out.println("\n***********************");

        System.out.println("\nSaldo do cartão: " +cartao.getSaldo());
