# Polimorfismo em Java

**Polimorfismo** significa "muitas formas". Em Java, isso permite que você use uma **mesma interface ou classe base** para representar diferentes tipos de objetos.

> Polimorfismo é quando um mesmo método pode se comportar de várias formas, dependendo de como ou por quem ele é chamado.
> 

Existem dois tipos principais de polimorfismo em Java:

- **Polimorfismo em tempo de compilação (ou estático)**
    
    ➤ Exemplo: **Sobrecarga de métodos** (*method overloading*)
    
- **Polimorfismo em tempo de execução (ou dinâmico)**
    
    ➤ Exemplo: **Sobrescrita de métodos** (*method overriding*)
    

## 1. Polimorfismo em Tempo de Compilação (Sobrecarga - Overloading)

Neste exemplo, vamos criar uma classe `Calculadora` com vários métodos `somar`, mas com assinaturas diferentes.

```java
public class Calculadora {

    // Soma dois inteiros
    public int somar(int a, int b) {
        System.out.println("Soma de inteiros:");
        return a + b;
    }

    // Soma três inteiros
    public int somar(int a, int b, int c) {
        System.out.println("Soma de três inteiros:");
        return a + b + c;
    }

    // Soma dois números decimais
    public double somar(double a, double b) {
        System.out.println("Soma de decimais:");
        return a + b;
    }

    public static void main(String[] args) {
        Calculadora calc = new Calculadora();

        System.out.println(calc.somar(2, 3));         // Chama versão int
        System.out.println(calc.somar(2, 3, 4));      // Chama versão 3 ints
        System.out.println(calc.somar(2.5, 3.7));     // Chama versão double
    }
}
```

A mesma classe define vários métodos com o mesmo nome, mas com diferentes tipos ou quantidades de parâmetros, e o compilador escolhe qual chamar.

- Chama-se Tempo de Compilação por que escolhe qual método somar usar baseado nos tipos e nas quantidades dos argumentos no momento da compilação.

## 2. Polimorfismo em Tempo de Execução (Sobrescrita - Overriding)

Vamos usar uma **classe base `Funcionario`** e duas subclasses `Gerente` e `Desenvolvedor`. Cada uma sobrescreve o método `calcularSalario()` de forma diferente.

```java
// Classe base
class Funcionario {
    protected String nome;
    protected double salarioBase;

    public Funcionario(String nome, double salarioBase) {
        this.nome = nome;
        this.salarioBase = salarioBase;
    }

    public double calcularSalario() {
        return salarioBase;
    }
}

// Subclasse Gerente
class Gerente extends Funcionario {
    private double bonus;

    public Gerente(String nome, double salarioBase, double bonus) {
        super(nome, salarioBase);
        this.bonus = bonus;
    }

    @Override
    public double calcularSalario() {
        return salarioBase + bonus;
    }
}

// Subclasse Desenvolvedor
class Desenvolvedor extends Funcionario {
    private int horasExtras;

    public Desenvolvedor(String nome, double salarioBase, int horasExtras) {
        super(nome, salarioBase);
        this.horasExtras = horasExtras;
    }

    @Override
    public double calcularSalario() {
        return salarioBase + (horasExtras * 50.0); // R$ 50 por hora extra
    }
}

// Classe principal
public class FolhaPagamento {
    public static void main(String[] args) {
        Funcionario f1 = new Gerente("Ana", 5000, 1500);
        Funcionario f2 = new Desenvolvedor("Carlos", 4000, 10);

        System.out.println("Salário de " + f1.nome + ": R$" + f1.calcularSalario());
        System.out.println("Salário de " + f2.nome + ": R$" + f2.calcularSalario());
    }
}
```

Uma subclasse modifica o comportamento de um método herdado para atender suas necessidades, e em tempo de execução o método certo é escolhido com base no tipo real do objeto.

- Chama-se tempo de execução por que o método sobrescrito chamado depende do tipo real do objeto (Gerente ou Desenvolvedor) em tempo de execução, mesmo que a variável seja do tipo 
(`Funcionario`).
