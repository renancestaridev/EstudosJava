# Pacotes e Importações em Java

Em Java, **pacotes (packages)** são usados para organizar o código em grupos lógicos, como se fossem pastas. Já as **importações (imports)** permitem usar classes de outros pacotes no seu programa. Isso torna o código mais limpo, organizado e reaproveitável.

### Como criar um Pacote

```java
// Arquivo: util/Calculadora.java
package util; // <- Define o pacote

public class Calculadora {
    public static int somar(int a, int b) {
        return a + b;
    }
}
```

Pacote é como uma "pasta" para organizar as classes.

### Como Importar um Pacote

```java
// Arquivo: App.java
import util.Calculadora; // <- Importa a classe Calculadora do pacote util

public class App {
    public static void main(String[] args) {
        int resultado = Calculadora.somar(5, 3);
        System.out.println("Resultado: " + resultado);
    }
}
```

Importamos para usar classes que estão em outros pacotes.

### Como usar Import com `*` (curinga)

```java
import java.util.*; // Importa todas as classes do pacote java.util

public class Teste {
    public static void main(String[] args) {
        ArrayList<String> nomes = new ArrayList<>();
        nomes.add("Ana");
        System.out.println(nomes);
    }
}
```

`*` importa todas as classes do pacote, mas não subpacotes.

### Como usar sem importação (mesmo pacote ou java.lang)

```java
// Arquivo: MinhaClasse.java (no mesmo pacote de App)
public class MinhaClasse {
    public void dizerOi() {
        System.out.println("Oi!");
    }
}

// Arquivo: App.java
public class App {
    public static void main(String[] args) {
        MinhaClasse obj = new MinhaClasse(); // mesma pasta = sem import
        obj.dizerOi();
    }
}
```

Se estiver no mesmo pacote, não precisa importar.

### Pacote `java.lang` é automático

```java
public class Exemplo {
    public static void main(String[] args) {
        String texto = "Olá";  // String faz parte de java.lang (não precisa importar)
        System.out.println(texto);
    }
}
```
