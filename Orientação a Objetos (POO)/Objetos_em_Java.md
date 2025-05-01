# Objetos em Java

### **O que são Objetos?**

- Em Java, **objetos** são instâncias de **classes**.
- Eles representam **entidades do mundo real** com **estado** (atributos) e **comportamento** (métodos).

> Exemplo real: um objeto Carro pode ter atributos como cor e velocidade, e métodos como acelerar() e frear().
> 

### **Classe vs Objeto**

- **Classe:** modelo/estrutura.
- **Objeto:** instância da classe.

```java
public class Carro {
    String cor;
    int velocidade;

    void acelerar() {
        velocidade += 10;
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        Carro meuCarro = new Carro(); // objeto
        meuCarro.cor = "Vermelho";
        meuCarro.acelerar();
        System.out.println(meuCarro.velocidade); // 10
    }
}
```

### **Componentes de um Objeto**

- **Atributos**: variáveis dentro da classe.

```java
public class Carro {
    String cor;  // Atributo
    int velocidade;  // Atributo
}
```

- **Métodos**: funções que definem o comportamento.

```java
public void acelerar() {
    velocidade += 10;
}
```

- **Construtor**: método especial usado para inicializar objetos.

```java
public Carro(String c) {
    cor = c;  // Inicializa o atributo cor com o valor passado
    velocidade = 0;  // Inicializa o atributo velocidade com 0
}
```

### **Palavra-chave `new`**

- Usada para criar um novo objeto:

```java
Carro carro1 = new Carro("Azul");
```

### **Encapsulamento (Boa prática)**

- Tornar os atributos `private` e acessá-los via **getters/setters**.

```java
public class Carro {
    private String cor;

    public Carro(String corInicial) {
        cor = corInicial;
    }

    public String getCor() {
        return cor;
    }

    public void setCor(String novaCor) {
        cor = novaCor;
    }
}
```

Comentários em código para melhor entendimento

```java
// Arquivo Carro.java
public class Carro { // Classe Carro - Define o comportamento e atributos de um carro

    // Atributos: variáveis dentro da classe que representam o estado do objeto
    private String cor; // Atributo cor: define a cor do carro (tipo String)
    private int velocidade; // Atributo velocidade: define a velocidade do carro (tipo int)

    // Construtor: método especial usado para inicializar o objeto (Carro)
    public Carro(String c) { // Construtor da classe Carro - Recebe um valor para a cor do carro
        cor = c; // Inicializa o atributo cor com o valor passado como argumento
        velocidade = 0; // Inicializa o atributo velocidade com o valor 0 (começa parado)
    }

    // Métodos: funções que definem o comportamento do objeto (Carro)

    public String getCor() { // Getter para acessar o valor do atributo cor
        return cor; // Retorna o valor armazenado no atributo cor
    }

    public void setCor(String novaCor) { // Setter para modificar o valor do atributo cor
        cor = novaCor; // Altera o valor do atributo cor para o novo valor recebido
    }

    public int getVelocidade() { // Getter para acessar o valor do atributo velocidade
        return velocidade; // Retorna o valor armazenado no atributo velocidade
    }

    public void acelerar() { // Método que aumenta a velocidade do carro
        velocidade += 10; // Incrementa a velocidade em 10 a cada chamada
    }

    public void frear() { // Método que diminui a velocidade do carro
        if (velocidade >= 10) { // Verifica se a velocidade é maior ou igual a 10
            velocidade -= 10; // Diminui a velocidade em 10
        }
    }

    public void exibirInfo() { // Método que exibe informações do carro
        System.out.println("Cor: " + cor + ", Velocidade: " + velocidade + " km/h"); // Exibe a cor e a velocidade do carro
    }
}

```

```java
// Arquivo Main.java
public class Main {
    public static void main(String[] args) {
        // Criando um objeto Carro
        Carro meuCarro = new Carro("Vermelho"); // A cor do carro é definida como "Vermelho"

        // Exibindo as informações iniciais
        meuCarro.exibirInfo(); // Esperado: Cor: Vermelho, Velocidade: 0 km/h

        // Acelerando o carro duas vezes
        meuCarro.acelerar();
        meuCarro.acelerar();
        meuCarro.exibirInfo(); // Esperado: Cor: Vermelho, Velocidade: 20 km/h

        // Freando o carro
        meuCarro.frear();
        meuCarro.exibirInfo(); // Esperado: Cor: Vermelho, Velocidade: 10 km/h
    }
}
```
