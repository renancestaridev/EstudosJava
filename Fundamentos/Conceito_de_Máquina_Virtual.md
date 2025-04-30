# Conceito de máquina virtual

# JVM - Java Virtual Machine

A **Java Virtual Machine (JVM)** é um componente da plataforma Java.

- Sua função é **executar projetos Java**.
- Garante que a execução seja feita **de maneira eficiente**.
- Permite que o programa seja **independente de plataforma**.

---

Quando um programa Java é escrito, o código fonte (`.java`) precisa ser **compilado**.

O compilador `**javac**` converte o código fonte Java em **bytecode**:

- **Bytecode** é um código intermediário que é armazenado em arquivos com a extensão `.class`.

Ou seja:

> O código Java é compilado para **bytecode**. Ao escrever um programa Java, você compila usando o compilador **javac**, que gera arquivos .**class** contendo o **bytecode**.
> 

---

# JDK - Java Development Kit

Enquanto a **JVM** apenas executa programas, o **JDK** (Java Development Kit) **permite desenvolver e executar** programas Java

Exemplo prático:

```jsx
javac HelloWorld.java   # Compila usando o compilador que vem no JDK
java HelloWorld         # Executa usando a JVM que vem no JDK
```

Se tivéssemos apenas a JVM instalada, **não teríamos o `javac`** e **não conseguiríamos compilar** o código.

---

# JRE - Java Runtime Environment

O **JRE** (Java Runtime Environment) é o **mínimo necessário** para **rodar** programas Java — **mas não serve para desenvolver**.

- Quando você instala o **JDK**, **ele já traz tudo o que o JRE oferece**.
- Se, por exemplo, você **precisa apenas rodar** um sistema bancário feito em Java, o **JRE é suficiente**.
- Mas se você **está criando** um sistema em Java, aí sim precisa do **JDK** para **escrever** e **compilar** o código.

---

### Em resumo:

- **JVM**: Só executa programas Java (roda o bytecode).
- **JRE**: Permite rodar programas Java (vem com JVM + bibliotecas).
- **JDK**: Permite desenvolver (compilar) e rodar (executar) programas Java (vem com JRE + ferramentas).
