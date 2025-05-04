# Construtores em Java

Um **construtor** é um método especial que é chamado automaticamente quando um objeto é criado. Ele **tem o mesmo nome da classe** e **não tem tipo de retorno** (nem `void`).

### Tipos de Construtores

### **1. Construtor Padrão (Default Constructor)**

- É aquele **sem parâmetros**.
- Se você não declarar nenhum construtor, o Java cria um construtor padrão automaticamente.
- Mas se você criar qualquer outro construtor, o padrão **não será mais gerado automaticamente**.

```java
class Pessoa {
    String nome;

    // Construtor padrão
    Pessoa() {
        nome = "Desconhecido";
    }
}
```

### **2. Construtor Parametrizado**

- Permite passar **valores** ao criar o objeto.

```java
class Pessoa {
    String nome;

    // Construtor parametrizado
    Pessoa(String nomeInformado) {
        nome = nomeInformado;
    }
}
```

**Exemplo completo**

```java
public class Pessoa {
    String nome;
    int idade;

    // Construtor padrão
    Pessoa() {
        nome = "Sem nome";
        idade = 0;
    }

    // Construtor parametrizado
    Pessoa(String nome, int idade) {
        this.nome = nome;
        this.idade = idade;
    }

    void mostrarDados() {
        System.out.println("Nome: " + nome);
        System.out.println("Idade: " + idade);
    }

    public static void main(String[] args) {
        Pessoa p1 = new Pessoa(); // Usa o construtor padrão
        Pessoa p2 = new Pessoa("Ana", 25); // Usa o construtor parametrizado

        p1.mostrarDados();
        System.out.println("-----");
        p2.mostrarDados();
    }
}
```

Saída

```java
Nome: Sem nome
Idade: 0
-----
Nome: Ana
Idade: 25
```

- `p1` usa o **construtor padrão**, que define nome = "Sem nome", idade = 0.
- `p2` usa o **construtor parametrizado**, que recebe `"Ana"` e `25`.
