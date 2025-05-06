# Encapsulamento em Java

Encapsulamento é a prática de **esconder os detalhes internos** de uma classe e **expor apenas o que for necessário**. Isso é feito usando **modificadores de acesso** (como `private`, `public`) e **métodos getters e setters**. Assim, os atributos só podem ser acessados e modificados de forma segura.

Exemplo simples de Encapsulamento em Java

```java
public class Pessoa {
    // Atributos privados
    private String nome;
    private int idade;

    // Construtor
    public Pessoa(String nome, int idade) {
        this.nome = nome;
        this.idade = idade;
    }

    // Getter para o nome
    public String getNome() {
        return nome;
    }

    // Setter para o nome
    public void setNome(String nome) {
        this.nome = nome;
    }

    // Getter para a idade
    public int getIdade() {
        return idade;
    }

    // Setter para a idade
    public void setIdade(int idade) {
        if (idade >= 0) {
            this.idade = idade;
        }
    }
}
```

- `private`: impede que outros acessem diretamente os atributos.
- `getNome()` e `setNome(...)`: permitem acesso controlado ao atributo `nome`.
- Com `setIdade(...)`, você pode validar a idade antes de alterá-la — essa é uma grande vantagem do encapsulamento.
- `get` e `set` podem incluir **regras de negócio**, como validações ou restrições — e isso é justamente uma das maiores vantagens do encapsulamento.

### Vantagens do Encapsulamento

- **Segurança**: protege os dados de acessos indevidos.
- **Controle**: você pode validar os dados antes de alterar.
- **Facilidade de manutenção**: se mudar a lógica interna, o resto do código não precisa mudar.
- **Modularidade**: o código fica mais organizado.

O encapsulamento é uma maneira de proteger os dados de um objeto, garantindo que eles só possam ser acessados ou modificados por meio de métodos controlados, que podem incluir regras, validações e restrições.

**Importante**

Encapsulamento **não significa criar `get` e `set` para tudo automaticamente**. O ideal é **expor apenas o que realmente precisa ser acessado ou alterado**. Se todos os atributos têm `get` e `set` públicos sem validação, o encapsulamento perde seu propósito.

## **Exemplo Prático**

**Classe `ContaBancaria` com Encapsulamento**

Proteger o saldo de uma conta bancária para que ele **só possa ser alterado de forma segura**, impedindo saques negativos ou depósitos inválidos.

```java
public class ContaBancaria {
    private String titular;
    private double saldo;

    public ContaBancaria(String titular, double saldoInicial) {
        this.titular = titular;
        if (saldoInicial >= 0) {
            this.saldo = saldoInicial;
        }
    }

    public String getTitular() {
        return titular;
    }

    public double getSaldo() {
        return saldo;
    }

    // Método para depositar
    public void depositar(double valor) {
        if (valor > 0) {
            saldo += valor;
        }
    }

    // Método para sacar
    public boolean sacar(double valor) {
        if (valor > 0 && valor <= saldo) {
            saldo -= valor;
            return true;
        }
        return false;
    }
}
```

- Os atributos `titular` e `saldo` estão **protegidos com `private`**.
- O método `getSaldo()` **permite consultar o saldo**, mas **não alterá-lo diretamente**.
- Os métodos `depositar()` e `sacar()` são as **únicas formas de mudar o saldo**, e **têm regras internas** para evitar erros (como depositar valores negativos ou sacar mais do que há disponível).
- **Encapsulamento em ação:** o objeto controla como os dados são usados, protegendo a lógica do sistema.

```java
public class Main {
    public static void main(String[] args) {
        ContaBancaria conta = new ContaBancaria("Renan", 500.0);

        System.out.println("Titular: " + conta.getTitular());
        System.out.println("Saldo inicial: " + conta.getSaldo());

        conta.depositar(200.0);
        System.out.println("Saldo após depósito: " + conta.getSaldo());

        boolean saque1 = conta.sacar(100.0);
        System.out.println("Saque de 100 realizado? " + saque1);
        System.out.println("Saldo após saque: " + conta.getSaldo());

        boolean saque2 = conta.sacar(700.0); // excede o saldo
        System.out.println("Saque de 700 realizado? " + saque2);
        System.out.println("Saldo final: " + conta.getSaldo());
    }
}

```

Saída

```java
Titular: Renan
Saldo inicial: 500.0
Saldo após depósito: 700.0
Saque de 100 realizado? true
Saldo após saque: 600.0
Saque de 700 realizado? false
Saldo final: 600.0
```
