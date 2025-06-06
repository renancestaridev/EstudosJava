# Exceções Personalizadas em Java

São classes que criamos para representar condições de erro específicas que não são cobertas pelas exceções padrão do Java, como `NullPointerException`, `IOException`, etc.

## Como Criar uma Exceção Personalizada?

### Herança

- **Checked Exception**: Herde de `Exception`.
- **Unchecked Exception**: Herde de `RuntimeException`.

A escolha depende se você quer **obrigar** (`checked`) ou **não obrigar** (`unchecked`) o tratamento da exceção.

Exemplo de Checked Exception (Obrigatória)

```java
// Criando a exceção personalizada
public class SaldoInsuficienteException extends Exception {
    public SaldoInsuficienteException(String mensagem) {
        super(mensagem);
    }
}
```

```java
// Usando a exceção
public class ContaBancaria {
    private double saldo;

    public ContaBancaria(double saldoInicial) {
        this.saldo = saldoInicial;
    }

    public void sacar(double valor) throws SaldoInsuficienteException {
        if (valor > saldo) {
            throw new SaldoInsuficienteException("Saldo insuficiente para o saque de R$ " + valor);
        }
        saldo -= valor;
    }
}
```

```java
// Tratando a exceção
public class Main {
    public static void main(String[] args) {
        ContaBancaria conta = new ContaBancaria(100);

        try {
            conta.sacar(200);
        } catch (SaldoInsuficienteException e) {
            System.out.println("Erro: " + e.getMessage());
        }
    }
}
```

Exceção personalizada que obriga tratamento, ideal para erros previsíveis e recuperáveis, como `SaldoInsuficienteException` usada para validar saldo antes de sacar.

Exemplo de Unchecked Exception (Opcional)

```java
public class IdadeInvalidaException extends RuntimeException {
    public IdadeInvalidaException(String mensagem) {
        super(mensagem);
    }
}
```

```java
public class Pessoa {
    private int idade;

    public void setIdade(int idade) {
        if (idade < 0) {
            throw new IdadeInvalidaException("Idade não pode ser negativa!");
        }
        this.idade = idade;
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        Pessoa p = new Pessoa();
        p.setIdade(-5);  // Vai lançar a exceção sem precisar de try-catch
    }
}
```

Exceção personalizada que não exige tratamento, usada para violações de regras internas ou erros de programação, como `IdadeInvalidaException` lançada ao definir idade negativa.

Estrutura recomendada de exceção personalizada

```java
public class MinhaExcecao extends Exception {
    public MinhaExcecao() {
        super();
    }

    public MinhaExcecao(String message) {
        super(message);
    }

    public MinhaExcecao(String message, Throwable cause) {
        super(message, cause);
    }

    public MinhaExcecao(Throwable cause) {
        super(cause);
    }
}
```

Modelo padrão de exceção personalizada com múltiplos construtores, garantindo flexibilidade para incluir mensagens e causas ao lançar ou propagar erros.
