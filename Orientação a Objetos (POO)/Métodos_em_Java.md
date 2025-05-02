# Métodos em Java

Um **método** é um bloco de código que executa uma tarefa específica. Ele pode ou não receber valores (parâmetros) e pode ou não retornar um resultado.

**Estrutura básica de um método em Java**

```java
modificador tipoDeRetorno nomeDoMetodo(parâmetros) {
    // corpo do método
}
```

Componentes:

- **Modificador de acesso** (ex: `public`, `private`)
- **Tipo de retorno**: tipo de dado que o método retorna (`int`, `String`, `void`, etc.)
- **Nome do método**: segue a convenção *camelCase*
- **Parâmetros (opcional)**: dados que o método recebe
- **Corpo**: o que o método faz

**Método que retorna um valor**

```java
public int somar(int a, int b) {
    return a + b;
}
```

Chamada do método

```java
int resultado = somar(5, 3); // resultado = 8
```

**Método que não retorna nada (`void`)**

```java
public void dizerOla() {
    System.out.println("Olá!");
}
```

Chamada

```java
dizerOla(); // Imprime: Olá!
```

**Método `main` (ponto de entrada do programa)**

```java
public class MeuPrograma {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

Dicas

- Métodos ajudam a **organizar** o código e **evitar repetição**.

Sem métodos (Repetição no Código)

```java
public class ExemploRepetido {
    public static void main(String[] args) {
        System.out.println("Olá, João!");
        System.out.println("Olá, Maria!");
        System.out.println("Olá, Ana!");
    }
}
```

Com método (mais limpo e reutilizável)

```java
public class ExemploComMetodo {
    public static void main(String[] args) {
        dizerOla("João");
        dizerOla("Maria");
        dizerOla("Ana");
    }

    public static void dizerOla(String nome) {
        System.out.println("Olá, " + nome + "!");
    }
}
```

- Um método pode chamar outro.

```java
public class ChamandoOutroMetodo {
    public static void main(String[] args) {
        iniciar(); // este método chama outros métodos
    }

    public static void iniciar() {
        saudacao();
        mostrarData();
    }

    public static void saudacao() {
        System.out.println("Bem-vindo ao sistema!");
    }

    public static void mostrarData() {
        System.out.println("Hoje é 29 de abril de 2025.");
    }
}
```

- Você pode ter métodos com o **mesmo nome**, desde que os parâmetros sejam diferentes (isso se chama **sobrecarga**).

```java
public class ExemploSobrecarga {
    public static void main(String[] args) {
        System.out.println(somar(5, 3));   // Chama o método que soma inteiros
        System.out.println(somar(4.5, 2.2));   // Chama o método que soma doubles
        System.out.println(somar(10));   // Chama o método que soma com valor padrão
    }

    public static int somar(int a, int b) {
        return a + b;
    }

    public static double somar(double a, double b) {
        return a + b;
    }

    public static int somar(int a) {
        return a + 0; // valor padrão 0
    }
}
```
