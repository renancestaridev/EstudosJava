# Herança em Java

Herança é o mecanismo pelo qual uma classe (chamada **subclasse** ou **classe derivada**) pode herdar características (métodos e atributos) de outra classe (chamada **superclasse** ou **classe base**).

```java
// Superclasse
class Animal {
    void fazerSom() {
        System.out.println("Algum som genérico");
    }
}

// Subclasse
class Cachorro extends Animal {
    void fazerSom() {
        System.out.println("Latido");
    }
}
```

`Cachorro` herda de `Animal` usando a palavra-chave `extends`. Ela pode sobrescrever (`override`) o método da superclasse.

- `extends`: usada para herdar de uma classe.
- `super`: usada para acessar membros da superclasse.
- `@Override`: anotação usada para indicar que um método está sobrescrevendo outro da superclasse.

## Conceito

Uma subclasse (ou classe derivada) herda métodos e atributos de uma superclasse (ou classe base), podendo sobrescrever os métodos herdados para alterar seu comportamento. No entanto, ela não é obrigada a manter o comportamento original, nem a ter um comportamento fixo.

Exemplo

```java
// Superclasse
class Animal {
    void emitirSom() {
        System.out.println("Som genérico de animal");
    }
}

// Subclasse que NÃO sobrescreve o método
class Cavalo extends Animal {
    // Herdando comportamento original de Animal
}

// Subclasse que SOBRESCREVE o método
class Gato extends Animal {
    @Override
    void emitirSom() {
        System.out.println("Miau");
    }
}

// Programa principal
public class Main {
    public static void main(String[] args) {
        Animal a = new Animal();
        Gato g = new Gato();
        Cavalo c = new Cavalo();

        a.emitirSom(); // Saída: Som genérico de animal
        g.emitirSom(); // Saída: Miau
        c.emitirSom(); // Saída: Som genérico de animal (herdado, sem sobrescrita)
    }
}
```

Importante

**Herança** permite reutilizar código de uma classe base, enquanto a **abstração** define um contrato que as subclasses devem obrigatoriamente implementar.
