# Try-catch em Java

Estrutura para tratamento de exceções, permite que o programa controle os erros, evitando falhas inesperadas que causem o encerramento do programa.

Estrutura básica do Try-catch

```java
try {
    // Código que pode lançar uma exceção
} catch (TipoDaExcecao e) {
    // Código que trata a exceção
} finally {
    // Código que sempre será executado (opcional)
}
```

Funcionamento

- **try**: Coloque aqui o código que pode gerar uma exceção.
- **catch**: Caso uma exceção ocorra no bloco `try`, o controle passa para o bloco `catch` correspondente, que trata a exceção.
- Pode haver **múltiplos `catch`** para diferentes exceções.
- **finally** (opcional): Bloco que sempre é executado, com ou sem exceção. Ideal para liberar recursos.

**Exemplo de uso simples**

```java
public class ExemploTryCatch {
    public static void main(String[] args) {
        try {
            int[] numeros = {1, 2, 3};
            System.out.println(numeros[5]); // Vai lançar ArrayIndexOutOfBoundsException
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Erro: índice fora do limite do array.");
        }
    }
}
```

Saída

```java
Erro: índice fora do limite do array.
```

**Exemplo com `finally`**

```java
public class ExemploFinally {
    public static void main(String[] args) {
        try {
            int resultado = 10 / 0; // ArithmeticException
        } catch (ArithmeticException e) {
            System.out.println("Erro: divisão por zero.");
        } finally {
            System.out.println("Este bloco sempre será executado.");
        }
    }
}
```

Saída

```java
Erro: divisão por zero.
Este bloco sempre será executado.
```

### Também é possível tratar múltiplas exceções

```java
try {
    String texto = null;
    System.out.println(texto.length());
} catch (NullPointerException e) {
    System.out.println("Erro: variável não pode ser nula.");
} catch (Exception e) {
    System.out.println("Erro genérico: " + e.getMessage());
}
```

Dessa forma, podemos tratar diferentes tipos de exceções separadamente, facilitando a identificação e o diagnóstico dos erros

## Onde usar `try-catch`

### 1. **Leitura de arquivos (IOException)**

Ex.: `FileReader`, `BufferedWriter` podem lançar `IOException`.

```java
import java.io.*;

public class ExemploArquivo {
    public static void main(String[] args) {
        try {
            BufferedReader reader = new BufferedReader(new FileReader("arquivo.txt"));
            System.out.println(reader.readLine());
            reader.close();
        } catch (IOException e) {
            System.out.println("Erro ao ler o arquivo: " + e.getMessage());
        }
    }
}
```

### 2. **Operação matemática arriscada (ArithmeticException)**

Ex.: Divisão por zero → `ArithmeticException`.

```java
public class ExemploMatematica {
    public static void main(String[] args) {
        try {
            int resultado = 10 / 0;
        } catch (ArithmeticException e) {
            System.out.println("Divisão por zero não permitida.");
        }
    }
}
```

### 3. **Acesso a arrays (ArrayIndexOutOfBoundsException)**

Ex.: Índices inválidos → `ArrayIndexOutOfBoundsException`.

```java
public class ExemploArray {
    public static void main(String[] args) {
        try {
            int[] numeros = {1, 2, 3};
            System.out.println(numeros[5]);
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Índice fora do limite do array.");
        }
    }
}
```

### 4. **Conversão de tipos (NumberFormatException)**

Ex.: `Integer.parseInt()` pode lançar `NumberFormatException`.

```java
public class ExemploConversao {
    public static void main(String[] args) {
        try {
            int numero = Integer.parseInt("abc");
        } catch (NumberFormatException e) {
            System.out.println("Erro na conversão de string para número.");
        }
    }
}
```

### 5. **Conexão com banco de dados (SQLException)**

Ex.: `SQLException` ao executar consultas.

```java
import java.sql.*;

public class ExemploBanco {
    public static void main(String[] args) {
        try {
            Connection conn = DriverManager.getConnection("jdbc:mysql://localhost/teste", "root", "senha");
            Statement stmt = conn.createStatement();
            stmt.executeQuery("SELECT * FROM tabela");
        } catch (SQLException e) {
            System.out.println("Erro no banco de dados: " + e.getMessage());
        }
    }
}
```

### 6. **Uso de API externa (Exception genérica)**

Ex.: Erros de rede ou resposta inválida.

```java
import java.net.*;

public class ExemploAPI {
    public static void main(String[] args) {
        try {
            URL url = new URL("https://api.exemplo.com/dados");
            url.openConnection().connect();
        } catch (Exception e) {
            System.out.println("Erro ao conectar na API: " + e.getMessage());
        }
    }
}
```

### 7. **Objeto nulo (NullPointerException)**

Evitar `NullPointerException`.

```java
public class ExemploNulo {
    public static void main(String[] args) {
        try {
            String texto = null;
            System.out.println(texto.length());
        } catch (NullPointerException e) {
            System.out.println("Objeto nulo detectado.");
        }
    }
}
```
