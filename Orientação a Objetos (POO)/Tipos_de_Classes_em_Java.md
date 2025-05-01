# Tipos de Classes em Java

# Classe Normal

Em Java, **todo arquivo `.java`** pode conter uma classe pública (`public class`) com o **mesmo nome** do arquivo.

> Exemplo: se o arquivo se chama Carro.java, dentro dele deve existir public class Carro.
> 

Você pode ter **outras classes** dentro do mesmo arquivo, mas **apenas uma pode ser `public`**.

Se aparecerem outras classes `public`, é porque elas vêm de **outros arquivos `.java`** separados (cada um com sua própria classe pública).

```java
// Arquivo: Carro.java
public class Carro {
    // Atributos (características do carro)
    String modelo;
    String cor;
    int ano;

    // Construtor (para criar um carro)
    public Carro(String modelo, String cor, int ano) {
        this.modelo = modelo;
        this.cor = cor;
        this.ano = ano;
    }

    // Método (ação do carro)
    public void exibirInformacoes() {
        System.out.println("Modelo: " + modelo);
        System.out.println("Cor: " + cor);
        System.out.println("Ano: " + ano);
    }
}
```

Exemplo de uso da classe

```java
// Arquivo: Main.java
public class Main {
    public static void main(String[] args) {
        Carro meuCarro = new Carro("Civic", "Preto", 2022);
        meuCarro.exibirInformacoes();
    }
}
```

Saída esperada

```java
Modelo: Civic
Cor: Preto
Ano: 2022
```

## Ponto importante:

- `Carro` é uma **classe normal** (não é `abstract`, `interface`, `enum`, nem interna).
- **Pode ser instanciada** usando `new Carro(...)`, o que é uma característica de uma **classe comum**.

# Classe Abstrata

Uma **classe abstrata** é uma classe que **não pode ser instanciada diretamente**.

Ela serve como **modelo** para outras classes que vão **herdar** dela.

- Usa-se a palavra-chave `abstract`.
- Pode ter **métodos normais** (com corpo) e **métodos abstratos** (sem corpo).
- Força as subclasses a **implementarem** os métodos abstratos.

Exemplo de Classe Abstrata

```java
// Arquivo: Animal.java
abstract class Animal {
    // Método abstrato (sem corpo)
    abstract void emitirSom();

    // Método normal (com corpo)
    void dormir() {
        System.out.println("Animal dormindo...");
    }
}
```

Exemplo de Subclasse

```java
// Arquivo: Cachorro.java
class Cachorro extends Animal {
    @Override
    void emitirSom() {
        System.out.println("O cachorro late: Au Au!");
    }
}

// Arquivo: Gato.java
class Gato extends Animal {
    @Override
    void emitirSom() {
        System.out.println("O gato mia: Miau!");
    }
}
```

Como usar?

```java
// Arquivo: Main.java
public class Main {
    public static void main(String[] args) {
        Animal cachorro = new Cachorro();
        Animal gato = new Gato();
        
        cachorro.emitirSom();  // Saída: O cachorro late: Au Au!
        gato.emitirSom();      // Saída: O gato mia: Miau!
        
        cachorro.dormir();     // Saída: Animal dormindo...
        gato.dormir();         // Saída: Animal dormindo...
    }
}
```

### **Resumindo**:

- **Métodos normais** (com corpo): Usados para comportamentos que são comuns a **todos** os tipos de animais.
    - Exemplo: `dormir()` — todos os animais dormem da mesma forma.
- **Métodos abstratos** (sem corpo): Usados para comportamentos que **variam** entre os tipos de animais.
    - Exemplo: `emitirSom()` — cada animal tem um som diferente.

### **Quando Usar**

- **Métodos normais**: Quando o comportamento é comum a todas as subclasses.
    - Exemplo: Todos os animais dormem da mesma forma, então a lógica de dormir é definida na classe abstrata.
- **Métodos abstratos**: Quando o comportamento varia de acordo com a subclasse.
    - Exemplo: Cada animal emite um som diferente, por isso o método `emitirSom()` é abstrato e deve ser implementado nas subclasses.

# Interface

No Java, **interface é tratada como um tipo especial de classe** — **mas** ela **não é uma classe normal**.

**interface é uma forma de aplicar o conceito de abstração** na programação orientada a objetos.

**Interface é algo que *nós* fazemos**.

- **Interface é algo que *nós* programadores criamos**.
- **Definimos** quais métodos (ações) ela deve ter.
- **Implementamos** a interface nas classes que precisam seguir aquele "contrato".

**Ou seja**, ela **não acontece sozinha**, **não é automática**.

É o programador quem escreve a interface e quem decide quando usar.

Exemplo de Interface

```java
// Arquivo Motorista.java
public interface Motorista {
    void ligarCarro();
    void acelerar();
}
```

```java
// Arquivo Pessoa.java
public class Pessoa implements Motorista {
    @Override
    public void ligarCarro() {
        System.out.println("Ligando o carro.");
    }

    @Override
    public void acelerar() {
        System.out.println("Acelerando o carro.");
    }
}
```

```java
// Arquivo Main.java
public class Main {
    public static void main(String[] args) {
        Pessoa pessoa = new Pessoa();
        pessoa.ligarCarro();
        pessoa.acelerar();
    }
}
```

**Explicação:**

- A interface `Motorista` **exige** que os métodos `ligarCarro` e `acelerar` existam.
- A classe `Pessoa` **é obrigada** a implementar todos os métodos definidos na interface.

**Comparação Interface vs Classe Abstrata**

- **Classe abstrata:**
    
    A pessoa **já sabe ligar o carro** (porque a classe abstrata pode trazer métodos prontos),
    
    **mas pode precisar aprender a dirigir** (implementando apenas o que falta).
    
- **Interface:**
    
    A pessoa **TEM que saber ligar o carro E dirigir**.
    
    **Nada vem pronto**, a classe precisa **implementar tudo**.
    

# Classe interna (Inner Class)

Uma **classe interna (inner class)** é uma classe definida dentro de outra classe. Em outras palavras, é uma classe que está aninhada dentro de uma classe externa.

**Características principais:**

- **Definida dentro de uma outra classe**.
- **Precisa** de uma instância da classe externa para ser criada.
- **Pode acessar** todos os membros (mesmo `private`) da classe externa.
- **Não pode ter membros `static`**, exceto constantes `static final`.
- A relação entre a interna e a externa é **forte** — como se a interna fosse "parte" da externa.

Exemplo

```java
// Arquivo Computador.java
public class Computador {
    private String marca = "TechMaster";

    // Classe interna
    class Processador {
        private String modelo = "i9-13900K";

        void detalhesProcessador() {
            System.out.println("Marca do computador: " + marca);
            System.out.println("Modelo do processador: " + modelo);
        }
    }

    public static void main(String[] args) {
        // Como criar objetos da Inner Class?
        // Passo 1: Criar uma instância da classe externa.
        Computador pc = new Computador();
        // Passo 2: Usar essa instância para criar a interna.
        Computador.Processador cpu = pc.new Processador();
        cpu.detalhesProcessador();
    }
}

```

Saída esperada

```java
Marca do computador: TechMaster
Modelo do processador: i9-13900K
```

Isso confirma que:

- Você criou a instância da classe externa (`pc = new Computador()`),
- Depois criou a instância da inner class (`cpu = pc.new Processador()`),
- E chamou o método `detalhesProcessador()`.

# Classe anônima (Anonymous class)

Classes anônimas são classes **sem nome**, usadas para **implementar interfaces** ou **estender classes abstratas** de forma **rápida e prática**.

Elas são úteis para evitar criar várias classes separadas quando você precisa de **comportamentos diferentes**.

Sintaxe básica

```java
TipoDeClasse nomeObjeto = new TipoDeClasse() {
    // Métodos sobrescritos
};
```

## Por que usar classe anônima?

- Para **criar implementações diferentes** sem precisar criar novas classes nomeadas.
- Para **reduzir código repetitivo**.
- Para deixar o código **mais direto e fácil de entender**.

Exemplo sem classe anônima (mais trabalhoso)

```java
class Ola implements Saudacao {
    public void cumprimentar() {
        System.out.println("Olá!");
    }
}

class BomDia implements Saudacao {
    public void cumprimentar() {
        System.out.println("Bom dia!");
    }
}

Saudacao ola = new Ola();
Saudacao bomDia = new BomDia();
```

Aqui criamos duas classes separadas só para mudar a saudação.

Exemplo com classe anônima (mais rápido)

```java
Saudacao ola = new Saudacao() {
    public void cumprimentar() {
        System.out.println("Olá!");
    }
};

Saudacao bomDia = new Saudacao() {
    public void cumprimentar() {
        System.out.println("Bom dia!");
    }
};
```

Aqui criamos as implementações na hora, direto no ponto onde vamos usar.

# Classe estática interna (Static nested class)

Em Java, uma **classe estática interna** é uma classe que está definida **dentro** de outra classe, mas que é marcada com o modificador `static`.

Diferente das **inner classes** comuns (não-estáticas), **ela não depende de uma instância da classe externa** para ser instanciada.

**Características principais**:

- Uma **classe interna comum** precisa de uma instância da classe externa.
- Uma **classe estática interna** **não precisa** — ela é associada diretamente à classe externa, **não** a uma instância.

```java
public class Externa {

    static class Interna {
        void mostrarMensagem() {
            System.out.println("Olá da classe interna estática!");
        }
    }

    public static void main(String[] args) {
        Externa.Interna obj = new Externa.Interna();
        obj.mostrarMensagem();
    }
}

// Saída
// Olá da classe interna estática!
```

### **Conceito**:

- Uma **classe estática interna** **fica dentro de outra classe**, mas **não precisa de instância** da classe externa para ser usada.
- A **classe interna estática** é usada quando ela **não depende dos dados ou comportamentos da classe externa**.

Uma **classe estática interna** é útil quando:

1. A classe interna **não precisa acessar membros** da instância da classe externa.
2. Você deseja **organizar o código** melhor, agrupando classes relacionadas sem precisar de um objeto da classe externa.
3. A classe interna serve mais como **um utilitário** ou **uma estrutura de dados auxiliar**.

# Classe local (Local class)

Uma **classe local** é uma **classe definida dentro de um método**. Ou seja, **é uma classe que existe apenas dentro do escopo de um método específico**.

Ela é útil quando você precisa de uma classe apenas temporariamente, apenas para ajudar em uma tarefa específica daquele método.

### Características principais da Classe Local:

- É **definida dentro de um método** (ou até dentro de um bloco como `if`, `for`, etc.).
- Só pode ser usada **dentro do próprio método** onde foi definida.
- Pode **acessar variáveis locais** do método, **desde que elas sejam `final` ou *effectively final*** (em Java 8+).
- Pode ter **métodos, atributos e construtores** como qualquer outra classe.
- Pode **estender** outra classe ou **implementar** interfaces.

Exemplo básico

```java
// Arquivo Exemplo.java
public class Exemplo {

    void meuMetodo() {
        // Definindo uma classe local
        class ClasseLocal {
            void mensagem() {
                System.out.println("Oi! Eu sou uma classe local.");
            }
        }

        // Criando um objeto da classe local
        ClasseLocal obj = new ClasseLocal();
        obj.mensagem();
    }

    public static void main(String[] args) {
        Exemplo exemplo = new Exemplo();
        exemplo.meuMetodo();
    }
}

// Saída
// Oi! Eu sou uma classe local.
```

Exemplo com acesso a variável local

```java
// Arquivo Exemplo2.java
public class Exemplo2 {

    void calculaQuadrado(int numero) {
        final int fator = 2;  // Ou poderia ser "effectively final"

        class Calculadora {
            int elevar() {
                return (int) Math.pow(numero, fator);
            }
        }

        Calculadora calc = new Calculadora();
        System.out.println("Resultado: " + calc.elevar());
    }

    public static void main(String[] args) {
        Exemplo2 exemplo = new Exemplo2();
        exemplo.calculaQuadrado(5);
    }
}

// Saída
// Resultado: 25
```

### Vantagens de usar uma Classe Local:

- **Organização**: Mantém o escopo restrito ao método onde ela é útil.
- **Leitura**: Deixa claro que a classe é usada apenas para aquela operação.
- **Evita poluir** o espaço de nomes da classe externa.

### Observações importantes:

- Ela **não pode ser pública, privada ou protegida** (não tem modificadores de acesso).
- Se você precisar acessar variáveis do método, elas precisam ser **final** ou **não modificadas depois de serem definidas**.

# Enumeração (enum)

É um tipo especial de classe usado para definir **conjuntos fixos de constantes**. Um `enum` oferece uma forma **segura e legível** de representar dados que possuem valores limitados.

Por exemplo, dias da semana, estados de um pedido (ABERTO, PROCESSANDO, FECHADO), cores, etc.

Sintaxe básica de um enum é

```java
public enum DiaDaSemana {
    SEGUNDA,
    TERCA,
    QUARTA,
    QUINTA,
    SEXTA,
    SABADO,
    DOMINGO
}
```

Cada valor listado (SEGUNDA, TERCA etc.) é uma constante do tipo DiaDaSemana.

O Enum fica em um arquivo separado (geralmente no mesmo pacote, ou num pacote de enums).
Você importa e usa ele em qualquer classe do projeto.
Isso deixa o código organizado e fácil de manter.
