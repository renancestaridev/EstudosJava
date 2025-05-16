# Listas em Java

## O que é uma Lista em Java?

Em Java, uma lista é uma **coleção de elementos**, como várias gavetas onde você pode guardar vários valores na ordem em que quiser, e acessar pelo índice (posição).

Exemplo

```java
[0] Maçã
[1] Banana
[2] Laranja
```

## `ArrayList` – Lista baseada em **array**

- Imagina um armário com gavetas.
- Cada gaveta tem um número (índice).
- O `ArrayList` é como esse armário: você guarda coisas nas gavetas e pega usando o número.

Exemplo básico

```java
import java.util.ArrayList;

public class ListaArrayList {
    public static void main(String[] args) {
        // Criando um ArrayList de frutas
        ArrayList<String> frutas = new ArrayList<>();

        // Adicionando elementos na lista
        frutas.add("Maçã");
        frutas.add("Banana");
        frutas.add("Laranja");

        // Acessando um elemento pelo índice (posição)
        System.out.println("Primeira fruta: " + frutas.get(0));

        // Removendo um item da lista
        frutas.remove("Banana");

        // Mostrando toda a lista
        System.out.println("Frutas restantes: " + frutas);
    }
}
```

**Exemplo prático com `ArrayList`**

Cadastro de nome de alunos

```java
import java.util.ArrayList;
import java.util.Scanner;

public class CadastroAlunos {
    public static void main(String[] args) {
        ArrayList<String> alunos = new ArrayList<>();
        Scanner scanner = new Scanner(System.in);

        System.out.println("Digite 3 nomes de alunos:");
        for (int i = 0; i < 3; i++) {
            System.out.print("Aluno " + (i+1) + ": ");
            String nome = scanner.nextLine();
            alunos.add(nome);
        }

        System.out.println("\nLista de alunos cadastrados:");
        for (String nome : alunos) {
            System.out.println("- " + nome);
        }

        scanner.close();
    }
}
```

## `LinkedList` – Lista ligada por "nós"

- Imagine um trem com vagões.
- Cada vagão sabe quem vem antes e quem vem depois.
- O `LinkedList` funciona assim: cada item é ligado ao anterior e ao próximo.

Exemplo básico

```java
import java.util.LinkedList;

public class ListaLinkedList {
    public static void main(String[] args) {
        // Criando uma LinkedList de tarefas
        LinkedList<String> tarefas = new LinkedList<>();

        // Adicionando tarefas
        tarefas.add("Estudar");
        tarefas.add("Fazer exercício");
        tarefas.addFirst("Acordar"); // Adiciona no início

        // Mostra a primeira tarefa
        System.out.println("Primeira tarefa: " + tarefas.getFirst());

        // Mostra todas as tarefas
        System.out.println("Tarefas do dia: " + tarefas);
    }
}
```

**Exemplo prático com `LinkedList`**

Fila de atendimento

```java
import java.util.LinkedList;
import java.util.Scanner;

public class FilaAtendimento {
    public static void main(String[] args) {
        LinkedList<String> fila = new LinkedList<>();
        Scanner scanner = new Scanner(System.in);

        // Adicionando pessoas na fila
        System.out.println("Digite 3 pessoas para entrar na fila:");
        for (int i = 0; i < 3; i++) {
            System.out.print("Pessoa " + (i+1) + ": ");
            String nome = scanner.nextLine();
            fila.addLast(nome); // Adiciona no final
        }

        // Simulando atendimento
        System.out.println("\nAtendendo pessoas:");
        while (!fila.isEmpty()) {
            String atendido = fila.removeFirst(); // Remove do início
            System.out.println("Atendendo: " + atendido);
        }

        scanner.close();
    }
}
```

- Use `ArrayList` se você precisa **acessar rápido** os elementos
- Use `LinkedList` se você precisa **inserir/remover muito** no meio ou começo.
