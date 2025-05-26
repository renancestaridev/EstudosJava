# Exceção em Java

**Exceção** (**Exception**) é um **evento anormal** que ocorre durante a execução do programa e que **interrompe o fluxo normal** das instruções. Quando ocorre um erro, Java cria um objeto que representa esse erro, chamado de **objeto de exceção**. Esse objeto contém informações sobre o erro, como o tipo e a causa.

Exemplo:

- Dividir um número por zero
- Tentar acessar um índice inválido em um array
- Tentar abrir um arquivo que não existe

### Divisão por zero

```java
public class Exemplo1 {
    public static void main(String[] args) {
        try {
            int resultado = 10 / 0;  // Vai dar erro!
            System.out.println("Resultado: " + resultado);
        } catch (ArithmeticException e) {
            System.out.println("Não pode dividir por zero.");
        }
    }
}
```

Saída

```java
Não pode dividir por zero.
```

### Acessando um índice fora do array

```java
public class Exemplo2 {
    public static void main(String[] args) {
        int[] numeros = {1, 2, 3};
        
        try {
            System.out.println(numeros[5]);  // Não existe posição 5
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Índice fora do array.");
        }
    }
}
```

Saída

```java
Índice fora do array.
```

### `finally` sempre executa

```java
public class Exemplo3 {
    public static void main(String[] args) {
        try {
            int x = 5 / 0;
        } catch (ArithmeticException e) {
            System.out.println("Erro de divisão por zero.");
        } finally {
            System.out.println("Esse bloco sempre aparece!");
        }
    }
}
```

Saída

```java
Erro de divisão por zero.
Esse bloco sempre aparece!
```

## Usado para tratar uma exceção

- `try` → tente executar este código → onde pode acontecer o erro
- `catch` → se der erro, pegue ele aqui → onde você resolve ou mostra a mensagem
- `finally` → sempre executa, com ou sem erro. (opcional) → sempre acontece, com erro ou não
