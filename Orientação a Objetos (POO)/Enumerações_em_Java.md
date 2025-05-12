# Enumerações em Java

As **enumerações** (ou *enums*) em Java são usadas para representar um **conjunto fixo de constantes com nome**. Elas são extremamente úteis quando precisamos trabalhar com valores bem definidos, como os dias da semana, status de um pedido, ou níveis de acesso de um usuário.

Elas tornam o código mais claro, seguro e fácil de manter, especialmente quando lidamos com **estados fixos e limitados** em um contexto específico.

### Conceitos Básicos de Enumerações em Java

### 1. **Declaração Simples de Enum**

```java
public enum DiaDaSemana {
    SEGUNDA, TERCA, QUARTA, QUINTA, SEXTA, SABADO, DOMINGO
}
```

Aqui, `DiaDaSemana` é um tipo com valores limitados que representam cada dia da semana.

### 2. **Uso Básico**

```java
DiaDaSemana hoje = DiaDaSemana.SEGUNDA;

if (hoje == DiaDaSemana.SEGUNDA) {
    System.out.println("Hoje é segunda-feira.");
}
```

Enums funcionam bem em comparações e estruturas de controle como `if` e `switch`.

### 3. Enum com Atributos, Construtor e Método

Você pode adicionar valores associados a cada constante:

```java
public enum StatusPedido {
    PENDENTE("Pendente"),
    PROCESSANDO("Em processamento"),
    ENVIADO("Enviado"),
    ENTREGUE("Entregue");

    private String descricao;

    // Construtor
    StatusPedido(String descricao) {
        this.descricao = descricao;
    }

    // Getter
    public String getDescricao() {
        return descricao;
    }
}
```

Exemplo de uso

```java
StatusPedido status = StatusPedido.ENVIADO;
System.out.println(status.getDescricao()); // Saída: Enviado
```

### 4. **Métodos Úteis com Enum**

- `values()` retorna todos os valores possíveis:

```java
for (StatusPedido status : StatusPedido.values()) {
    System.out.println(status);
}
```

Obter um valor específico a partir do nome

```java
StatusPedido status = StatusPedido.valueOf("PENDENTE");
```

Se o nome passado não corresponder exatamente ao nome de uma constante, uma exceção será lançada.

### Comportamento Específico por Constante

Enums também podem ter **métodos diferentes para cada constante**. Isso é útil quando cada valor precisa agir de forma única.

```java
public enum NivelUsuario {
    MASTER {
        public void mostrarPermissoes() {
            System.out.println("MASTER: Acesso total ao sistema.");
        }
    },
    GERENTE {
        public void mostrarPermissoes() {
            System.out.println("GERENTE: Acesso a relatórios e gestão.");
        }
    },
    FUNCIONARIO {
        public void mostrarPermissoes() {
            System.out.println("FUNCIONARIO: Acesso básico.");
        }
    };

    // Método abstrato obrigatório em cada constante
    public abstract void mostrarPermissoes();
}
```

Exemplo de uso

```java
NivelUsuario nivel = NivelUsuario.GERENTE;
nivel.mostrarPermissoes(); // GERENTE: Acesso a relatórios e gestão.
```

### Enums Implementando Interfaces

Enums também podem **implementar interfaces**, o que permite que sejam tratados de forma polimórfica — como qualquer outra classe Java.

Interface

```java
public interface Permissoes {
    void mostrarPermissoes();
}
```

Enum que implementa a interface

```java
public enum NivelUsuario implements Permissoes {
    MASTER {
        public void mostrarPermissoes() {
            System.out.println("MASTER: Acesso total.");
        }
    },
    GERENTE {
        public void mostrarPermissoes() {
            System.out.println("GERENTE: Acesso a relatórios.");
        }
    },
    FUNCIONARIO {
        public void mostrarPermissoes() {
            System.out.println("FUNCIONARIO: Acesso restrito.");
        }
    }
}
```

Uso com Polimorfismo

```java
public class Sistema {
    public static void imprimirPermissao(Permissoes permissao) {
        permissao.mostrarPermissoes();
    }

    public static void main(String[] args) {
        imprimirPermissao(NivelUsuario.MASTER); // Funciona com qualquer valor do enum
    }
}
```

## Boas Práticas com Enums

- Use enums para representar **categorias fixas e finitas**
- Prefira enums ao invés de `String` ou `int` quando os valores são conhecidos
- Evite lógica complexa diretamente dentro de enums — delegue para classes se necessário
- Use interfaces quando precisar de **flexibilidade e reaproveitamento**
