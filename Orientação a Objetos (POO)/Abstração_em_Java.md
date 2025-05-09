# Abstração em Java

**Abstração** é o processo de esconder detalhes complexos e mostrar apenas as funcionalidades essenciais de um objeto.

- Através de **classes abstratas**
- Através de **interfaces**

### Classe Abstrata

Uma **classe abstrata** serve como uma **base comum** para outras classes. Ela pode conter tanto métodos com implementação (comportamento comum), quanto métodos abstratos (que obrigam as subclasses a fornecerem sua própria implementação).

N**ão pode criar uma instância diretamente** de uma classe abstrata. Ela serve como um modelo para outras classes.

```java
abstract class Animal {
    String nome;

    Animal(String nome) {
        this.nome = nome;
    }

    abstract void emitirSom(); // cada animal vai implementar à sua maneira

    void dormir() {
        System.out.println(nome + " está dormindo.");
    }
}

class Cachorro extends Animal {
    Cachorro(String nome) {
        super(nome);
    }

    @Override
    void emitirSom() {
        System.out.println(nome + " diz: Au Au!");
    }
}

class Gato extends Animal {
    Gato(String nome) {
        super(nome);
    }

    @Override
    void emitirSom() {
        System.out.println(nome + " diz: Miau!");
    }
}

public class TesteAnimal {
    public static void main(String[] args) {
        Animal cachorro = new Cachorro("Rex");
        Animal gato = new Gato("Mimi");

        cachorro.emitirSom(); // Rex diz: Au Au!
        gato.emitirSom();     // Mimi diz: Miau!
        gato.dormir();        // Mimi está dormindo.
    }
}
```

Neste exemplo, `Animal` define um comportamento comum (`dormir`) e obriga os filhos a implementarem `emitirSom()`. Cada animal faz isso de forma diferente — o que representa bem a abstração.

### Interface

Uma **interface** define um **contrato de comportamento**: ela diz *"o que uma classe deve fazer"*, mas **não diz como**. Ou seja, ela não fornece implementação dos métodos (exceto se forem `default` ou `static`, a partir do Java 8).

Interfaces **não têm atributos com estado** nem construtores. No entanto, uma classe pode **implementar quantas interfaces quiser**, o que permite flexibilidade.

```java
interface Voavel {
    void voar(); // método obrigatório
}

class Passaro implements Voavel {
    @Override
    public void voar() {
        System.out.println("O pássaro está voando.");
    }
}

class Aviao implements Voavel {
    @Override
    public void voar() {
        System.out.println("O avião está voando.");
    }
}

public class TesteInterface {
    public static void main(String[] args) {
        Voavel objeto1 = new Passaro();
        Voavel objeto2 = new Aviao();

        objeto1.voar(); // O pássaro está voando.
        objeto2.voar(); // O avião está voando.
    }
}
```

Neste caso, `Passaro` e `Aviao` **não têm nada em comum em termos de estrutura**, mas ambos **compartilham o comportamento de voar**, o que é perfeitamente representado por uma interface.
