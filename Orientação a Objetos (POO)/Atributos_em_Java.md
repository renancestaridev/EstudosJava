# Atributos em Java

Em Java, **atributos** (ou **variáveis de instância**) são **características** de um objeto. Eles representam **dados** que cada instância (objeto) de uma classe pode ter.

Exemplo

```java
public class Pessoa {
    String nome;         // atributo
    int idade;           // atributo
}
```

Nesse exemplo, `nome` e `idade` são atributos da classe `Pessoa`. Cada `Pessoa` criada terá o seu próprio nome e idade.

### Em Java, os **tipos de atributos** podem ser classificados de **duas formas diferentes**

## 1. **Por comportamento no código (função dentro da classe)**

**Atributo de instância**

```java
public class Pessoa {
    String nome;  // cada objeto Pessoa terá seu próprio nome
}
```

Se você criar 2 objetos, cada um tem seu próprio valor:

```java
Pessoa p1 = new Pessoa();
Pessoa p2 = new Pessoa();
p1.nome = "Ana";
p2.nome = "Carlos";
```

**Atributo de classe (`static`)**

```java
public class Contador {
    static int total = 0; // compartilhado por todos os objetos

    public void incrementar() {
        total++;
    }
}
```

É o mesmo para todos. Se um objeto muda ele, todos veem essa mudança:

```java
public class Teste {
    public static void main(String[] args) {
        Contador c1 = new Contador();
        Contador c2 = new Contador();

        c1.incrementar();  // total agora é 1
        c2.incrementar();  // total agora é 2

        System.out.println(Contador.total); // imprime: 2
    }
}
```

Atributo constante (`final`)

```java
public class Configuracao {
    public static final String VERSAO = "1.0.0";
}
```

`static + final` → constante. O valor não pode ser alterado:

```java
// Configuracao.VERSAO = "2.0"; // ERRO! não pode alterar uma constante
```

## 2. **Por persistência ou uso especial**

Esses são menos comuns, mas importantes em projetos mais avançados.

`transient`

```java
transient String senha;
```

Quando você grava o objeto em arquivo ou transmite pela rede (**serialização**), esse atributo será **ignorado**.

`volatile`

```java
volatile boolean ativo;
```

Usado em aplicações com **multithreading**, garantindo que mudanças feitas por uma thread fiquem visíveis para outras.
