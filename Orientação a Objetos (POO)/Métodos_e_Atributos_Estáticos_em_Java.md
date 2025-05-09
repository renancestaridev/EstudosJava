# Métodos e Atributos estáticos

### O que é `static` em Java?

Em Java, quando um **atributo ou método é declarado como `static`**, ele **pertence à classe**, e não às instâncias (objetos) dessa classe.

### Atributos Estáticos

Um atributo estático é declarado como `public static int contador;`, o que faz com que ele pertença à classe e não a um objeto específico. Todas as instâncias compartilham o mesmo valor desse atributo, que pode ser acessado diretamente usando o nome da classe, como em `MinhaClasse.contador = 10;`. Mesmo quando subclasses utilizam esse atributo herdado, elas acessam o mesmo valor compartilhado da superclasse — não há duplicação nem sobrescrita, apenas um único valor comum entre todas as classes da hierarquia.

Exemplo Acesso de atributo estático por superclasse e subclasse

```java
// Classe base com atributo estático
public class Conta {
    public static int totalContas = 0;

    public Conta() {
        totalContas++; // Incrementa sempre que uma nova conta é criada
    }
}
// Subclasse que herda de Conta
public class ContaCorrente extends Conta {
    public ContaCorrente() {
        super(); // Também incrementa o totalContas
    }
}
```

```java
// Classe principal com o main
public class Banco {
    public static void main(String[] args) {
        // Criando objetos de diferentes classes
        Conta c1 = new Conta();
        ContaCorrente cc1 = new ContaCorrente();
        ContaCorrente cc2 = new ContaCorrente();

        // Acessando o atributo estático
        System.out.println("Total de contas criadas: " + Conta.totalContas); // Saída: 3
        System.out.println("Acesso via subclasse: " + ContaCorrente.totalContas); // Também: 3
    }
}
```

- `totalContas` é um atributo estático da classe `Conta`.
- Cada vez que um objeto de `Conta` ou `ContaCorrente` é criado, ele é incrementado.
- Mesmo acessando por `ContaCorrente`, o valor é o **mesmo**, pois o atributo é **único e compartilhado**.
- Não há duplicação ou sobrescrita, apenas **um contador global**.

### Métodos Estáticos

Um método estático pode ser chamado sem a necessidade de criar uma instância da classe. No entanto, ele **não pode acessar diretamente atributos ou métodos não estáticos**, pois esses dependem de uma instância específica da classe, e métodos estáticos não têm acesso a essa instância.

```java
public class Pessoa {
    public String nome = "Renan"; // não estático

    public static void saudacao() {
        // System.out.println("Olá, " + nome); // ❌ ERRO! 'nome' não é estático
        System.out.println("Olá!");
    }
}
```

Correto

```java
Pessoa.saudacao(); // Não precisa de objeto
```

Importante

- `static` define membros de **classe**, e não de objeto.
- Atributos estáticos são úteis para dados **compartilhados globalmente**.
- Métodos estáticos devem ser usados quando a lógica **não depende de atributos ou comportamentos de instância**.
