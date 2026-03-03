# BancoJava


public class Conta {
     private String titular;
      private double saldo;

  public Conta(String titular) {
        this.titular = titular;
         this.saldo = 0.0;
    }

  public String getTitular() {
        return titular;
    }

  public double getSaldo() {
        return saldo;
    }

  public void depositar(double valor) {
        if (valor > 0) {
             saldo += valor;
              System.out.println("Depósito realizado com sucesso!");
        } else {
            System.out.println("Valor inválido!");
        }
    }

  public void sacar(double valor) {
        if (valor > saldo) {
            System.out.println("Saldo insuficiente!");
        } else if (valor <= 0) {
            System.out.println("Valor inválido!");
        } else {
            saldo -= valor;
            System.out.println("Saque realizado com sucesso!");
        }
    }

  public void exibirSaldo() {
        System.out.println("Titular: " + titular);
         System.out.println("Saldo atual: R$ " + saldo);
    }
}


import java.util.Scanner;

public class Main {
    public static void main(String[] args) {

  Scanner scanner = new Scanner(System.in);

  System.out.println(" SISTEMA BANCÁRIO ");
     System.out.print("Digite o nome do titular: ");
        String nome = scanner.nextLine();

  Conta conta = new Conta(nome);

   int opcao;

   do {
            System.out.println("\n1 - Depositar");
             System.out.println("2 - Sacar");
              System.out.println("3 - Ver saldo");
               System.out.println("0 - Sair");
                System.out.print("Escolha uma opção: ");
                opcao = scanner.nextInt();

  switch (opcao) {
                case 1:
                    System.out.print("Digite o valor para depósito: ");
                     double deposito = scanner.nextDouble();
                      conta.depositar(deposito);
                         break;

  case 2:
         System.out.print("Digite o valor para saque: ");
                double saque = scanner.nextDouble();
                    conta.sacar(saque);
                    break;

   case 3:
         conta.exibirSaldo();
               break;

  case 0:
       System.out.println("Encerrando sistema...");
                    break;

  default:
  System.out.println("Opção inválida!");
}

 } while (opcao != 0);

   scanner.close();
    }
}
