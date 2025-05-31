# Finally em Java

`Finally` é opcional e é usado junto com `try` e possivelmente `catch`. Ele sempre é executado após o bloco `try`, independentemente de uma exceção ter sido lançada ou capturada.

Estrutura

```java
try {
    // Código que pode lançar exceção
} catch (ExceptionType e) {
    // Tratamento da exceção
} finally {
    // Código que sempre será executado
}
```

**Executado quando**

- Se **não ocorrer exceção**, o `finally` é executado após o `try`.
- Se **ocorrer exceção e for tratada** com `catch`, o `finally` é executado após o `catch`.
- Se **ocorrer exceção e não for tratada** no `catch`, o `finally` ainda assim é executado antes de o programa terminar ou a exceção ser propagada.
- Mesmo com comandos como `return`, `break` ou `continue` dentro do `try` ou `catch`, o `finally` será executado.

Exemplo prático

```java
public class ExemploFinally {
    public static void main(String[] args) {
        try {
            System.out.println("Dentro do try");
            int resultado = 10 / 0; // Lança ArithmeticException
        } catch (ArithmeticException e) {
            System.out.println("Exceção capturada: " + e.getMessage());
        } finally {
            System.out.println("Bloco finally executado");
        }
    }
}
```

Saída

```java
Dentro do try
Exceção capturada: / by zero
Bloco finally executado
```

**Usar o `finally` quando**

- Para **fechar recursos** como arquivos, conexões de banco de dados, ou fluxos de entrada/saída.
- Para **liberar memória** ou **resetar valores** importantes.
- Para garantir a **finalização de processos críticos**.

## Exemplo com `finally` e `return`

```java
public class ExemploReturn {
    public static void main(String[] args) {
        System.out.println(metodo());
    }

    static String metodo() {
        try {
            System.out.println("Try");
            return "Retorno do try";
        } finally {
            System.out.println("Finally");
        }
    }
}
```

Saída

```java
Try
Finally
Retorno do try
```

Mesmo com o `return` no `try`, o `finally` ainda é executado.
