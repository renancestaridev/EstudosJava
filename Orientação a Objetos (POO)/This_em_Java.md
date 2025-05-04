# This em Java

Em Java, a palavra-chave `this` é usada para referenciar o objeto atual da classe.

## 1. **`this.atributo` — Acessar o atributo da instância**

Usado quando o nome do **atributo** e o nome do **parâmetro** são iguais. O `this` diferencia o que é da **classe** e o que é do **método**.

```java
public class Pessoa {
    String nome;

    public Pessoa(String nome) {
        this.nome = nome; // 'this.nome' = atributo | 'nome' = parâmetro
    }
}
```

## 2. **`this.metodo()` — Chamar um método da mesma classe**

Podemos usar `this` para chamar **outros métodos da própria classe** (como se estivesse dizendo: “eu mesmo vou executar este método”).

```java
public class Aluno {
    void estudar() {
        System.out.println("Estudando...");
    }

    void rotina() {
        this.estudar(); // chama o método estudar()
    }
}
```

## 3. **`this()` — Chamar outro construtor da mesma classe**

Se a classe tiver **mais de um construtor**, você pode usar `this(...)` para reaproveitar código.

```java
public class Pessoa {
    String nome;
    int idade;

    public Pessoa(String nome) {
        this(nome, 0); // chama o segundo construtor
    }

    public Pessoa(String nome, int idade) {
        this.nome = nome;
        this.idade = idade;
    }
}
```

Quando um objeto pode ser criado com **informações completas ou parciais**, você usa `this(...)` para **definir valores padrão** e manter a lógica centralizada.

## 4. **`return this` — Retornar o próprio objeto**

Útil para encadear métodos (method chaining).

```java
public class Produto {
    String nome;
    double preco;

    // Método que define o nome e retorna o objeto atual
    public Produto setNome(String nome) {
        this.nome = nome;
        return this;
    }

    // Método que define o preço e retorna o objeto atual
    public Produto setPreco(double preco) {
        this.preco = preco;
        return this;
    }

    // Método comum para mostrar os dados
    public void mostrar() {
        System.out.println("Produto: " + nome + " - R$" + preco);
    }
}
```

Uso com encadeamento de métodos:

```java
public class Main {
    public static void main(String[] args) {
        Produto p1 = new Produto();

        p1.setNome("Caneta")
          .setPreco(2.50)
          .mostrar();
    }
}
```

- Cada método `setNome()` e `setPreco()` retorna `this`, ou seja, o próprio `p1`.
- Isso permite **chamar vários métodos na mesma linha**, como uma "corrente" p1.setNome("Caneta").setPreco(2.50);

## 5. **`this` como referência (avançado)**

Você pode passar `this` como **referência ao próprio objeto** para outro método ou classe.

```java
public class Pessoa {
    String nome;

    public Pessoa(String nome) {
        this.nome = nome;
    }

    // Método que imprime o nome
    public void imprimir() {
        System.out.println("Nome: " + nome);
    }

    // Envia o próprio objeto como argumento
    public void executar() {
        Util.mostrar(this); // 'this' aqui é o próprio objeto Pessoa
    }
}
```

```java
// Classe separada com método que recebe um objeto Pessoa
public class Util {
    public static void mostrar(Pessoa p) {
        p.imprimir(); // chama o método imprimir da instância recebida
    }
}
```

Uso

```java
public class Main {
    public static void main(String[] args) {
        Pessoa p1 = new Pessoa("Renan");
        p1.executar(); // Saída: Nome: Renan
    }
}
```

- `this` é passado como argumento para outro método (`Util.mostrar(this)`).
- O método externo (`mostrar`) recebe a instância e pode trabalhar com ela.

Permite **compartilhar o objeto atual** entre diferentes métodos e classes.
