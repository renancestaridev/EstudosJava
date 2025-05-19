# Conjuntos (Set) em Java

Set é uma coleção onde **não pode ter itens duplicados**.

Todos os tipos de `Set` ignoram automaticamente elementos duplicados.

### 1. `HashSet` – Rápido, mas desorganizado

Exemplo: Alunos colocam sugestões em uma urna, mas o professor só quer ver as ideias **sem se importar com a ordem** nem com repetições.

```java
import java.util.HashSet;
import java.util.Set;

public class CaixaSugestoes {
    public static void main(String[] args) {
        Set<String> sugestoes = new HashSet<>();

        // Alunos enviando sugestões
        sugestoes.add("Mais aulas práticas");
        sugestoes.add("Excursão escolar");
        sugestoes.add("Mais aulas práticas"); // Repetido, será ignorado
        sugestoes.add("Lanches melhores");

        System.out.println("Sugestões recebidas:");
        for (String sugestao : sugestoes) {
            System.out.println("- " + sugestao);
        }
    }
}
```

### Quando usar:

- Quando **não se importa com a ordem** dos elementos.
- Quando **precisa de rapidez**.
- Quando **não quer duplicatas**.

### 2. `LinkedHashSet` – Organizado pela ordem que chegou

Exemplo: Registro de **ordem de chegada** dos funcionários. Nomes duplicados não entram.

```java
import java.util.LinkedHashSet;
import java.util.Set;

public class ListaPresenca {
    public static void main(String[] args) {
        Set<String> presenca = new LinkedHashSet<>();

        presenca.add("Roberto");
        presenca.add("Juliana");
        presenca.add("Roberto"); // Ignorado, já registrado
        presenca.add("Marcos");

        System.out.println("Ordem de chegada:");
        for (String nome : presenca) {
            System.out.println("- " + nome);
        }
    }
}
```

### Quando usar:

- Quando você quer **manter a ordem de inserção**.
- Quando também não quer repetição.
- Exemplo: registrar a ordem de chegada dos funcionários.

### 3. `TreeSet` – Sempre em ordem alfabética (ou numérica)

Exemplo: Criar uma lista de contatos que já fica **em ordem alfabética automaticamente**.

```java
import java.util.Set;
import java.util.TreeSet;

public class AgendaTelefonica {
    public static void main(String[] args) {
        Set<String> contatos = new TreeSet<>();

        contatos.add("Carlos");
        contatos.add("Amanda");
        contatos.add("Bruno");
        contatos.add("Amanda"); // Repetido, ignorado

        System.out.println("Contatos na agenda:");
        for (String nome : contatos) {
            System.out.println("- " + nome);
        }
    }
}
```

### Quando usar:

- Quando você **precisa que tudo fique ordenado automaticamente**.
- Quando você **não pretende usar `null`**, pois `TreeSet` **não permite elementos nulos** (lança exceção).
- Pode usar um **`Comparator`** para definir uma outra ordem (como por tamanho da string, ou por sobrenome).
- Exemplo: lista de alunos por ordem alfabética.
