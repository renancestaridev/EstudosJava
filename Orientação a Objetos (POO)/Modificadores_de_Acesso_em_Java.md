# Modificadores de acesso em Java

São palavras-chave usadas para definir o **nível de visibilidade** (ou acesso) de classes, métodos, construtores e atributos. Eles controlam quem pode acessar determinado membro de uma classe e ajudam a implementar o encapsulamento, um dos pilares da programação orientada a objetos.

**`public`**

- Acesso liberado para **qualquer outra classe**.
- Pode ser acessado de qualquer lugar do código.

Exemplo

```java
public class MinhaClasse {
    public int numero;
    public void mostrar() {}
}
```

**`private`**

- Acesso permitido **somente dentro da própria classe**.
- Usado para esconder detalhes internos da implementação.

Exemplo

```java
public class MinhaClasse {
    private int segredo;
    private void metodoSecreto() {}
}
```

**`protected`**

- Acesso permitido **dentro do mesmo pacote** e **por subclasses** (mesmo que estejam em pacotes diferentes).
- Muito usado na herança.

Exemplo

```java
protected int valor;
protected void metodoProtegido() {}
```

**(sem modificador)** – *default* ou *package-private*

- Acesso permitido **apenas dentro do mesmo pacote**.
- Se você não escrever nenhum modificador, esse será o comportamento padrão.

Exemplo

```java
int idade; // acesso default
void metodoPadrao() {}
```

## Exemplo mais completo com **quatro classes diferentes**, distribuídas em dois pacotes, para demonstrar o comportamento real dos modificadores de acesso em Java

Estrutura de pacotes

```java
/pacote1
   ├── ClasseBase.java
   └── ClasseMesma.java

/pacote2
   ├── SubClasse.java
   └── ClasseFora.java
```

`ClasseBase.java` (em `pacote1`)

```java
package pacote1;

public class ClasseBase {
    public String publico = "Público";
    protected String protegido = "Protegido";
    String padrao = "Padrão (sem modificador)";
    private String privado = "Privado";

    public void mostrarAcessos() {
        System.out.println(publico);    // ok
        System.out.println(protegido); // ok
        System.out.println(padrao);    // ok
        System.out.println(privado);   // ok
    }
}
```

`ClasseMesma.java` (em `pacote1`)

```java
package pacote1;

public class ClasseMesma {
    public void testar() {
        ClasseBase obj = new ClasseBase();
        System.out.println(obj.publico);    // ok
        System.out.println(obj.protegido); // ok
        System.out.println(obj.padrao);    // ok
        // System.out.println(obj.privado); // ERRO: privado, não acessível
    }
}
```

`SubClasse.java` (em `pacote2`)

```java
package pacote2;
import pacote1.ClasseBase;

public class SubClasse extends ClasseBase {
    public void testar() {
        System.out.println(publico);     // ok
        System.out.println(protegido);  // ok (acessado por herança)
        // System.out.println(padrao);   // ERRO: default (não é acessível fora do pacote)
        // System.out.println(privado);  // ERRO: privado, não acessível
    }
}
```

`ClasseFora.java` (em `pacote2`)

```java
package pacote2;
import pacote1.ClasseBase;

public class ClasseFora {
    public void testar() {
        ClasseBase obj = new ClasseBase();
        System.out.println(obj.publico);    // ok
        // System.out.println(obj.protegido); // ERRO: só subclasses acessam protegido fora do pacote
        // System.out.println(obj.padrao);    // ERRO: default, não acessível fora do pacote
        // System.out.println(obj.privado);   // ERRO: privado
    }
}
```
