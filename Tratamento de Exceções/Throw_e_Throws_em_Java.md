# Throw e Throws em Java

### `throw`: Para lançar uma exceção

Serve para **lançar uma exceção e interromper a execução do programa** quando acontecer algo de errado

Por exemplo, o cliente solicita sacar mais dinheiro do que possui na conta

Exemplo de um Sistema Bancário / Saque

```java
public class ContaBancaria {
    private double saldo;

    public ContaBancaria(double saldoInicial) {
        this.saldo = saldoInicial;
    }

    public void sacar(double valor) {
        if (valor > saldo) {
            // ERRO: lançar uma exceção
            throw new IllegalArgumentException("Saldo insuficiente para saque.");
        }
        saldo -= valor;
        System.out.println("Saque realizado com sucesso. Saldo atual: " + saldo);
    }

    public static void main(String[] args) {
        ContaBancaria conta = new ContaBancaria(100);
        conta.sacar(150);  // Aqui vai lançar a exceção
    }
}
```

Se a pessoa tentar sacar mais do que tem, o programa **lança** (`throw`) uma exceção e **para** ali.

### `throws`: Para avisar que pode acontecer uma exceção

Serve para **avisar que um método pode gerar um problema (exceção)** e quem for usar deve tratar ou repassar esse erro.

Exemplo de Abrir um Arquivo

```java
import java.io.*;

public class LeitorDeArquivo {
    public void lerArquivo(String nomeDoArquivo) throws IOException {
        // Pode dar erro se o arquivo não existir
        BufferedReader br = new BufferedReader(new FileReader(nomeDoArquivo));
        String linha = br.readLine();
        System.out.println("Primeira linha: " + linha);
        br.close();
    }

    public static void main(String[] args) {
        LeitorDeArquivo leitor = new LeitorDeArquivo();
        try {
            leitor.lerArquivo("meuarquivo.txt");
        } catch (IOException e) {
            System.out.println("Erro ao ler o arquivo: " + e.getMessage());
        }
    }
}
```

O método `lerArquivo` avisa com `throws` que pode dar erro.

Quem chama (`main`) precisa tratar com `try-catch`.
