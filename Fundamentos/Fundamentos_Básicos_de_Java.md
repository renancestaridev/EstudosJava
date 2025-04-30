# Fundamentos básicos de Java

# Estrutura básica de um programa Java

Exemplo básico

```java
public class MeuPrograma {
    public static void main(String[] args) {
        System.out.println("Olá, mundo!");
    }
}
```

1. **`public class MeuPrograma`**
    - Define uma **classe pública** chamada `MeuPrograma`.
    - O nome do arquivo deve ser o mesmo da classe (ex: `MeuPrograma.java`).
2. **`public static void main(String[] args)`**
    - Esse é o ponto de entrada do programa.
    - O Java sempre começa a execução por esse método.
    - `String[] args` serve para passar argumentos pela linha de comando (pode ficar vazio se não for usar).
3. **`System.out.println("Olá, mundo!");`**
    - Imprime uma linha de texto no console.
    - `System` é uma classe, `out` é um objeto que representa a saída padrão (geralmente a tela), e `println` é um método que imprime com quebra de linha.

**Importante**

- O nome **`main.java` não é obrigatório** e nem padrão.
- O importante é: o arquivo **tem que ter o mesmo nome da classe pública** que contém o método `main`.

Programas mais complexos podem ter

```java
package com.exemplo.app;

import java.util.Scanner;

public class App {
    public static void main(String[] args) {
        Scanner entrada = new Scanner(System.in);
        System.out.print("Digite seu nome: ");
        String nome = entrada.nextLine();
        System.out.println("Olá, " + nome);
    }
}
```

Quanto mais pacotes, importações e uso de objetos, maior será o programa.

# Tipos primitivos

Em Java, os tipos primitivos são 8, e eles não são objetos — são os blocos de construção para dados simples.

### 1. **`int`**

- **Uso mais comum** para números inteiros.
- Ex: contadores, IDs, idade, quantidade.

```java
int idade = 25;
int numeroDeTentativas = 3;
```

### 2. **`long`**

- Quando espera **números inteiros muito grandes** (maiores que 2 bilhões).
- Ex: CPF, CNPJ, número de cartão, timestamps.

```java
long cpf = 12345678901L;
```

### 3. **`float`** e **`double`**

- Para **números com casas decimais**.
- `float` = menos preciso e mais leve.
- `double` = mais preciso, padrão para decimais.
- Ex: preço, nota, média.

```java
float preco = 9.99f;
double salario = 3450.75;
```

### 4. **`char`**

- Armazena **um único caractere**.
- Ex: letra inicial, gênero, tipo de perfil ('A', 'B', 'C').
- ❌ Não recomendado para nome de usuário (melhor `String`).

```java
char genero = 'M'; // M ou F
```

### 5. **`boolean`**

- Verdadeiro ou falso.
- Ex: usuário ativo, login bem-sucedido, tem permissão.

```java
boolean isLogado = true;
boolean isAdmin = false;
```

### 6. **`byte` e `short`**

- Usados quando quer **economizar memória**, e sabe que os valores vão ser pequenos.
- Ex: status (0, 1), idade se muitos registros.

```java
byte status = 1;  // 1 = ativo, 0 = inativo
short anoNascimento = 1990;
```

Importante

- Tipos primitivos são **mais rápidos** e consomem menos memória que objetos.
- Eles **não podem ser nulos**, exceto quando usados em wrappers (como `Integer`, `Double` etc.).
- Para números grandes, use `long` com **"L" no final** (ex: `123456789L`).
- `float` deve ter **"f" no final** (ex: `3.14f`), senão será considerado `double`.

# Variáveis

Variáveis são espaços na memória usados para armazenar dados temporariamente durante a execução de um programa.

Exemplo de como declarar

```java
tipo nomeDaVariavel = valor;
```

Exemplo

```java
int idade = 25;
double altura = 1.75;
String nome = "Renan";
```

### Tipos mais comuns:

- `int` – números inteiros
- `double` – números com ponto flutuante
- `boolean` – `true` ou `false`
- `char` – um único caractere (`'a'`, `'b'`)
- `String` – texto (objeto, não tipo primitivo)

# Constantes

Constantes são variáveis que não podem ter seu valor alterado depois de serem atribuídas. Em Java, usamos a palavra-chave **final** para isso.

Exemplo de como declarar

```java
final tipo NOME_DA_CONSTANTE = valor;
```

nomes de constantes são escritos em **letras maiúsculas**.

Exemplo

```java
final double PI = 3.14159;
final int MAX_TENTATIVAS = 5;
```

Se você tentar alterar o valor depois, causará um erro de compilação:

```java
PI = 3.14; // ERRO!
```

Importante

- Uma variável `final` deve ser **inicializada** no momento da declaração ou no **construtor**, se for parte de uma classe.
- Uma vez atribuído, o valor não pode mudar.

Dica

- **Variável comum** = pode mudar (variável = variável).
- **`final`** = valor fixo (final = fim = imutável).

# Operadores

Os operadores são símbolos que realizam operações em variáveis e valores. Eles podem ser divididos em várias categorias, dependendo do tipo de operação que realizam.

### 1. **Operadores Aritméticos**

Esses operadores são usados para realizar operações matemáticas.

**+** (adição): Soma dois operandos.

```java
int a = 5 + 3;  // a = 8
```

**-** (subtração): Subtrai o segundo operando do primeiro.

```java
int a = 5 - 3;  // a = 2
```

***** (multiplicação): Multiplica dois operandos.

```java
int a = 5 * 3;  // a = 15
```

**/** (divisão): Divide o primeiro operando pelo segundo.

```java
int a = 6 / 3;  // a = 2
```

**%** (módulo): Retorna o resto da divisão do primeiro operando pelo segundo.

```java
int a = 5 % 3;  // a = 2
```

### 2. **Operadores de Atribuição**

Usados para atribuir valores a variáveis.

**=**: Atribui um valor à variável.

```java
int a = 10;  // a = 10
```

**+=**: Soma o valor da direita ao valor da esquerda e atribui o resultado à variável da esquerda.

```java
a += 5;  // a = a + 5
```

**-=**: Subtrai o valor da direita do valor da esquerda e atribui o resultado à variável da esquerda.

```java
a -= 3;  // a = a - 3
```

***=**: Multiplica o valor da esquerda pelo valor da direita e atribui o resultado à variável da esquerda.

```java
a *= 2;  // a = a * 2
```

**/=**: Divide o valor da esquerda pelo valor da direita e atribui o resultado à variável da esquerda.

```java
a /= 4;  // a = a / 4
```

### 3. **Operadores de Comparação**

Esses operadores são usados para comparar dois valores.

**==**: Verifica se os valores dos dois operandos são iguais.

```java
if (a == b) { // a é igual a b
```

**!=**: Verifica se os valores dos dois operandos são diferentes.

```java
if (a != b) { // a é diferente de b
```

**>**: Verifica se o valor do operando da esquerda é maior que o da direita.

```java
if (a > b) { // a é maior que b
```

**<**: Verifica se o valor do operando da esquerda é menor que o da direita.

```java
if (a < b) { // a é menor que b
```

**>=**: Verifica se o valor do operando da esquerda é maior ou igual ao da direita.

```java
if (a >= b) { // a é maior ou igual a b
```

**<=**: Verifica se o valor do operando da esquerda é menor ou igual ao da direita.

```java
if (a <= b) { // a é menor ou igual a b
```

### 4. **Operadores Lógicos**

Esses operadores são usados para realizar operações lógicas.

**&&** (AND lógico): Retorna `true` se ambos os operandos forem `true`.

```java
if (a > 5 && b < 10) { // verifica se a > 5 E b < 10
```

**||** (OR lógico): Retorna `true` se pelo menos um dos operandos for `true`.

```java
if (a > 5 || b < 10) { // verifica se a > 5 OU b < 10
```

**!** (NOT lógico): Inverte o valor lógico de um operando.

```java
if (!(a > 5)) { // verifica se NÃO a > 5
```

### 5. **Operadores de Incremento e Decremento**

Esses operadores aumentam ou diminuem o valor de uma variável.

**++ (incremento): Aumenta o valor de uma variável em 1.**

**Prefixo**: A variável é incrementada antes da expressão ser avaliada.

```java
int a = 5;
int b = ++a;  // a = 6, b = 6
```

**Pósfixo**: A variável é incrementada após a expressão ser avaliada.

```java
int a = 5;
int b = a++;  // a = 6, b = 5
```

**-- (decremento): Diminui o valor de uma variável em 1.**

**Prefixo**: A variável é decrementada antes da expressão ser avaliada.

```java
int a = 5;
int b = --a;  // a = 4, b = 4
```

**Pósfixo**: A variável é decrementada após a expressão ser avaliada.

```java
int a = 5;
int b = a--;  // a = 4, b = 5
```

### 6. **Operadores de Bit a Bit**

Esses operadores realizam operações em nível de bit.

**&** (AND bit a bit): Realiza a operação AND entre dois números.

```java
int a = 5 & 3;  // a = 1 (0101 & 0011 = 0001)
```

**|** (OR bit a bit): Realiza a operação OR entre dois números.

```java
int a = 5 | 3;  // a = 7 (0101 | 0011 = 0111)
```

**^** (XOR bit a bit): Realiza a operação XOR entre dois números.

```java
int a = 5 ^ 3;  // a = 6 (0101 ^ 0011 = 0110)
```

**~** (NOT bit a bit): Inverte todos os bits de um número.

```java
int a = ~5;  // a = -6 (inverte os bits de 0101)
```

**<<** (deslocamento à esquerda): Desloca os bits de um número para a esquerda.

```java
int a = 5 << 1;  // a = 10 (0101 << 1 = 1010)
```

**>>** (deslocamento à direita): Desloca os bits de um número para a direita.

```java
int a = 5 >> 1;  // a = 2 (0101 >> 1 = 0010)
```

**>>>** (deslocamento à direita sem sinal): Desloca os bits de um número para a direita, preenchendo com 0 à esquerda.

```java
int a = -5 >>> 1;  // a = 2147483642
```

### 7. **Operadores Ternários**

O operador ternário é uma forma compacta de um **if-else**.

**? :** Avalia uma expressão e retorna um valor com base no resultado.

```java
int a = (b > 5) ? 10 : 20;  // Se b > 5, a = 10, senão a = 20
```

### 8. **Operadores de Tipo**

Esses operadores são usados para realizar operações relacionadas ao tipo de dados.

**instanceof**: Verifica se um objeto é uma instância de uma classe ou interface.

```java
if (obj instanceof String) {  // Verifica se obj é uma instância de String
```

# Controle de fluxo

Permite controlar a ordem de execução das instruções com base em condições e repetições.

### 1. **Instruções Condicionais**

Usadas para executar código com base em condições.

### `if`, `else if`, `else`

```java
int idade = 18;

if (idade >= 18) {
    System.out.println("Maior de idade");
} else {
    System.out.println("Menor de idade");
}
```

### `switch`

Ideal para múltiplas condições baseadas em valores fixos.

```java
int dia = 3;

switch (dia) {
    case 1:
        System.out.println("Domingo");
        break;
    case 2:
        System.out.println("Segunda");
        break;
    default:
        System.out.println("Outro dia");
}
```

### 2. **Laços de Repetição (Loops)**

### `for`

Usado quando o número de repetições é conhecido.

```java
for (int i = 0; i < 5; i++) {
    System.out.println("Contador: " + i);
}
```

### `while`

Usado quando a condição de parada é verificada antes de cada repetição.

```java
int i = 0;
while (i < 5) {
    System.out.println("i = " + i);
    i++;
}
```

### `do...while`

Executa o bloco **pelo menos uma vez** antes de verificar a condição.

```java
int i = 0;
do {
    System.out.println("i = " + i);
    i++;
} while (i < 5);
```

### 3. **Comandos de Controle de Loop**

- `break`: Sai do loop imediatamente.
- `continue`: Pula para a próxima iteração do loop.

```java
for (int i = 0; i < 5; i++) {
    if (i == 2) continue;
    if (i == 4) break;
    System.out.println(i);
}
```

### **4. Controle de Fluxo com Exceções**

`try`, `catch`, `finally`, `throw`, `throws`

```java
try {
    int resultado = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Erro: " + e.getMessage());
} finally {
    System.out.println("Sempre executa");
}
```

Dica

Controle de fluxo também se estende a estruturas como exceções (try-catch), mas esses são tratados como parte do tratamento de erros.

# Array

### Arrays de Uma Dimensão (Vetores)

Um array é uma estrutura de dados que armazena vários valores do mesmo tipo em uma única variável.

Exemplo

```java
public class ExemploArraySimples {
    public static void main(String[] args) {
        int[] numeros = new int[5]; // declara um array de 5 inteiros

        // Atribuindo valores
        numeros[0] = 10;
        numeros[1] = 20;
        numeros[2] = 30;
        numeros[3] = 40;
        numeros[4] = 50;

        // Exibindo os valores
        for (int i = 0; i < numeros.length; i++) {
            System.out.println("Elemento na posição " + i + ": " + numeros[i]);
        }
    }
}
```

importante

- Os índices começam em `0`.
- O tamanho do array é fixo após a criação.
- Você pode usar um **loop `for`** ou **`for-each`** para percorrer arrays.

Exemplo com `for-each`:

```java
for (int numero : numeros) {
    System.out.println("Valor: " + numero);
}
```

### Sistema simples para armazenar e analisar as **temperaturas máximas da semana** em uma cidade.

1. Armazenar as temperaturas.
2. Calcular a média da semana.
3. Descobrir o maior e o menor valor.

```java
import java.util.Scanner;

public class TemperaturasSemana {
    public static void main(String[] args) {
        double[] temperaturas = new double[7];
        Scanner scanner = new Scanner(System.in);
        
        // Inserindo temperaturas
        for (int i = 0; i < temperaturas.length; i++) {
            System.out.print("Informe a temperatura do dia " + (i + 1) + ": ");
            temperaturas[i] = scanner.nextDouble();
        }

        // Calculando média, maior e menor
        double soma = 0;
        double maior = temperaturas[0];
        double menor = temperaturas[0];

        for (double temp : temperaturas) {
            soma += temp;
            if (temp > maior) maior = temp;
            if (temp < menor) menor = temp;
        }

        double media = soma / temperaturas.length;

        // Exibindo resultados
        System.out.println("\nMédia da semana: " + media + "°C");
        System.out.println("Maior temperatura: " + maior + "°C");
        System.out.println("Menor temperatura: " + menor + "°C");
    }
}
```

- Como armazenar vários valores relacionados (temperaturas da semana).
- Como percorrer o array para fazer cálculos.
- Como usar arrays para resolver problemas reais com eficiência.

### Arrays Multidimensionais (Matrizes)

Um array multidimensional é basicamente um **array de arrays**.
Exemplo de matriz 2D (2 linhas x 3 colunas):

```java
public class ExemploMatriz {
    public static void main(String[] args) {
        int[][] matriz = {
            {1, 2, 3},
            {4, 5, 6}
        };

        // Percorrendo a matriz
        for (int i = 0; i < matriz.length; i++) {
            for (int j = 0; j < matriz[i].length; j++) {
                System.out.print(matriz[i][j] + " ");
            }
            System.out.println(); // nova linha após cada linha da matriz
        }
    }
}
```

- `matriz.length` → número de linhas.
- `matriz[i].length` → número de colunas da linha `i`.

### Sistema de Notas de Alunos

- Armazenar as notas em uma **matriz**.
- Calcular a média de cada aluno.
- Mostrar todas as notas organizadas.

Código em Java (matriz 3x4)

```java
import java.util.Scanner;

public class NotasAlunos {
    public static void main(String[] args) {
        double[][] notas = new double[3][4]; // 3 alunos, 4 provas
        Scanner scanner = new Scanner(System.in);

        // Inserindo notas
        for (int aluno = 0; aluno < notas.length; aluno++) {
            System.out.println("Digite as notas do Aluno " + (aluno + 1) + ":");
            for (int prova = 0; prova < notas[aluno].length; prova++) {
                System.out.print("Nota da Prova " + (prova + 1) + ": ");
                notas[aluno][prova] = scanner.nextDouble();
            }
        }

        System.out.println("\n--- Médias dos Alunos ---");
        for (int aluno = 0; aluno < notas.length; aluno++) {
            double soma = 0;
            for (int prova = 0; prova < notas[aluno].length; prova++) {
                soma += notas[aluno][prova];
            }
            double media = soma / notas[aluno].length;
            System.out.println("Aluno " + (aluno + 1) + " - Média: " + media);
        }

        System.out.println("\n--- Tabela de Notas ---");
        for (int aluno = 0; aluno < notas.length; aluno++) {
            System.out.print("Aluno " + (aluno + 1) + ": ");
            for (int prova = 0; prova < notas[aluno].length; prova++) {
                System.out.print(notas[aluno][prova] + " ");
            }
            System.out.println();
        }
    }
}
```

- `double[][] notas` → uma **matriz** onde cada linha representa um aluno e cada coluna uma prova.
- Dois **loops aninhados** para preencher e percorrer a matriz.
- Cálculo de **média por linha** (aluno).

# Métodos

## Declaração e Chamada de Métodos

Declaração de método 
Quando você **cria** o método (define o que ele faz).

```java
public static void saudacao() {
    System.out.println("Olá, mundo!");
}
```

Chamada do método

Quando você **usa** o método.

```java
public class Main {
    public static void main(String[] args) {
        saudacao();  // Chamada do método
    }

    public static void saudacao() {
        System.out.println("Olá, mundo!");
    }
}
```

## Parâmetros e Retorno

Método com parâmetros

São **informações enviadas** para o método.

`String nome` é o **parâmetro**.

```java
public static void saudacao(String nome) {
    System.out.println("Olá, " + nome + "!");
}
```

Método com retorno

É o **valor que o método devolve**.

O método retorna um `int`.

```java
public static int somar(int a, int b) {
    return a + b;
}
```

Usando ambos

```java
public class Main {
    public static void main(String[] args) {
        saudacao("Maria");
        int resultado = somar(3, 5);
        System.out.println("Resultado: " + resultado);
    }

    public static void saudacao(String nome) {
        System.out.println("Olá, " + nome + "!");
    }

    public static int somar(int a, int b) {
        return a + b;
    }
}
```

Resumindo

- **Parâmetro** = entrada
- **Retorno** = saída

## Sobrecarga de Métodos (Overloading)

A sobrecarga ocorre quando **vários métodos têm o mesmo nome**, mas com **parâmetros diferentes** (tipo ou quantidade).

```java
public class Calculadora {
    public static int somar(int a, int b) {
        return a + b;
    }

    public static double somar(double a, double b) {
        return a + b;
    }

    public static int somar(int a, int b, int c) {
        return a + b + c;
    }

    public static void main(String[] args) {
        System.out.println(somar(2, 3));         // Chama o 1º método
        System.out.println(somar(2.5, 3.1));     // Chama o 2º método
        System.out.println(somar(1, 2, 3));      // Chama o 3º método
    }
}
```
