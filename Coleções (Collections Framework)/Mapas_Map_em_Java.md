# Mapas (Map) em Java

um mapa (ou Map) é uma estrutura de dados que armazena pares de chave e valor.
Ou seja: cada chave aponta para um valor.

Imagine uma **agenda de contatos**:

- O **nome da pessoa** é a **chave**
- O **número de telefone** é o **valor**

Exemplo

```java
"Maria" → "99999-1111"
"Renan"  → "98888-2222"
```

No Java, isso vira

```java
Map<String, String> agenda = new HashMap<>();
agenda.put("Maria", "99999-1111");
agenda.put("Renan", "98888-2222");
```

Com mapas é possível

- **Adicionar** uma entrada: `put(chave, valor)`
- **Pegar** um valor: `get(chave)`
- **Remover** uma entrada: `remove(chave)`
- **Verificar** se uma chave existe: `containsKey(chave)`
- **Ver todas as chaves**: `keySet()`
- **Ver todos os valores**: `values()`

Exemplo simples

```java
import java.util.HashMap;
import java.util.Map;

public class ExemploMap {
    public static void main(String[] args) {
        Map<String, Integer> idade = new HashMap<>();

        // Adiciona pessoas e suas idades
        idade.put("Lucas", 25);
        idade.put("Ana", 30);
        idade.put("Pedro", 20);

        // Pega a idade de Ana
        System.out.println("Idade da Ana: " + idade.get("Ana"));

        // Verifica se Pedro está no mapa
        if (idade.containsKey("Pedro")) {
            System.out.println("Pedro está no mapa!");
        }

        // Percorre todas as entradas
        for (String nome : idade.keySet()) {
            System.out.println(nome + " tem " + idade.get(nome) + " anos.");
        }
    }
}
```

Um **Map** é como uma **tabela** onde cada linha tem uma **chave única** (como o nome de uma pessoa) e um **valor** (como a idade dela ou telefone).

### `HashMap` – Rápido, mas sem ordem

Um **mapa desorganizado** mas **muito rápido**. Ideal quando você **não se importa com a ordem** dos dados, só quer acessá-los rapidamente.

Exemplo: Guardar o número de produtos vendidos por nome

```java
import java.util.HashMap;

public class ExemploHashMap {
    public static void main(String[] args) {
        HashMap<String, Integer> vendas = new HashMap<>();
        vendas.put("Maçã", 50);
        vendas.put("Banana", 30);
        vendas.put("Laranja", 20);

        System.out.println(vendas); // Pode aparecer fora de ordem
    }
}
```

Usar quando

- Precisa de performance (rápido)
- Não liga pra ordem dos dados

### `TreeMap` – Sempre ordenado (por chave)

Um mapa que **organiza os dados automaticamente em ordem crescente** pela **chave** (ordem alfabética, numérica, etc).

Exemplo: Guardar nomes de alunos e suas notas, e mostrar **em ordem alfabética**

```java
import java.util.TreeMap;

public class ExemploTreeMap {
    public static void main(String[] args) {
        TreeMap<String, Double> notas = new TreeMap<>();
        notas.put("Carlos", 7.5);
        notas.put("Ana", 8.0);
        notas.put("Bruno", 9.0);

        System.out.println(notas); // {Ana=8.0, Bruno=9.0, Carlos=7.5}
    }
}
```

Usar quando

- Precisa ver os dados **ordenados**
- Quer que o mapa **se organize automaticamente**

### `LinkedHashMap` – Mantém a ordem de inserção

Um mapa que **mantém os dados na ordem em que foram adicionados**.

Exemplo: Registrando os **pedidos em um restaurante**, e quer que apareçam na **ordem que foram feitos**

```java
import java.util.LinkedHashMap;

public class ExemploLinkedHashMap {
    public static void main(String[] args) {
        LinkedHashMap<Integer, String> pedidos = new LinkedHashMap<>();
        pedidos.put(1, "Pizza");
        pedidos.put(2, "Lasanha");
        pedidos.put(3, "Hambúrguer");

        System.out.println(pedidos); // {1=Pizza, 2=Lasanha, 3=Hambúrguer}
    }
}
```

Usar quando

- Quer manter a ordem de inserção
- Precisa de desempenho razoável + organização
