import java.util.Scanner;

abstract class Veiculo {
  double peso;
  double precoPorHora;

  public Veiculo(double peso) {
    this.peso = peso;
  }

  public abstract double getPrecoPorHora();

  public boolean podeEstacionar() {
    return true;
  }
}

class Motocicleta extends Veiculo {
  public Motocicleta(double peso) {
    super(peso);
  }

  @Override
  public double getPrecoPorHora() {
    if (peso <= 100) {
      return 2.00;
    } else if (peso <= 299.9) {
      return 4.00;
    } else {
      return 10.00;
    }
  }

  @Override
  public boolean podeEstacionar() {
    return peso <= 300;
  }
}

class CarroDePasseio extends Veiculo {
  public CarroDePasseio(double peso) {
    super(peso);
  }

  @Override
  public double getPrecoPorHora() {
    return 15.00;
  }

  @Override
  public boolean podeEstacionar() {
    return peso <= 2000;
  }
}

class Caminhonete extends Veiculo {
  public Caminhonete(double peso) {
    super(peso);
  }

  @Override
  public double getPrecoPorHora() {
    if (peso <= 3000) {
      return 25.00;
    } else {
      return 50.00;
    }
  }

  @Override
  public boolean podeEstacionar() {
    return peso <= 6000;
  }
}

class Furgao extends Veiculo {
  public Furgao(double peso) {
    super(peso);
  }

  @Override
  public double getPrecoPorHora() {
    if (peso <= 3000) {
      return 25.00;
    } else {
      return 50.00;
    }
  }

  @Override
  public boolean podeEstacionar() {
    return peso <= 6000;
  }
}

public class Estacionamento {
  public static void main(String[] args) {
    Scanner scanner = new Scanner(System.in);
    String opcao = "";

    while (!opcao.equals("sair")) {
      System.out.println("Deseja informar um novo veículo ou sair?");
      opcao = scanner.nextLine();

      if (opcao.equals("novo")) {
        System.out.println("Informe o tipo do veículo (motocicleta, carro, caminhonete, furgao):");
        String tipo = scanner.nextLine();
        System.out.println("Informe o peso do veículo:");
        double peso = scanner.nextDouble();
        scanner.nextLine();

        Veiculo veiculo;
        switch (tipo) {
          case "motocicleta":
            veiculo = new Motocicleta(peso);
            break;
          case "carro":
            veiculo = new CarroDePasseio(peso);
            break;
          case "caminhonete":
            veiculo = new Caminhonete(peso);
            break;
          case "furgao":
            veiculo = new Furgao(peso);
            break;
          default:
            System.out.println("Tipo de veículo desconhecido.");
            continue;
        }

        if (veiculo.podeEstacionar()) {
          System.out.println("O veículo pode ser estacionado. O valor por hora é R$ " + veiculo.getPrecoPorHora());
        } else {
          System.out.println("O veículo não pode ser estacionado.");
        }
      }
    }

    scanner.close();
  }
}
