# Iterações sobre Coleções em Java

**Iteração** significa "percorrer elemento por elemento" de uma coleção (por exemplo: `List`, `Set`, `Map`).

**Coleções** são estruturas que guardam múltiplos elementos, como listas de nomes, números, etc.

**Iterar sobre uma coleção** quer dizer **passar por cada elemento**, geralmente para ler, modificar ou realizar alguma ação com ele.

Exemplo de coleção

```java
List<String> nomes = new ArrayList<>();
nomes.add("Ana");
nomes.add("João");
nomes.add("Maria");
```

Quando iteramos, podemos **somar**, **imprimir**, **listar**, **verificar condições**, etc.

## For-each (ou enhanced for)

**For-each** é a maneira **mais simples e limpa** de iterar.

Mais simples, menos códigos e evita erros de índice.

Como funciona

```java
for (Tipo elemento : coleção) {
    // ação com elemento
}
```

Exemplo, imprimindo nomes

```java
for (String nome : nomes) {
    System.out.println("Olá, " + nome);
}
```

Saída

```java
Olá, Ana
Olá, João
Olá, Maria
```

**Usar quando:** quer apenas percorrer todos os elementos.

**Não permite modificar** a coleção diretamente (não pode usar `remove()` dentro dele).

## For tradicional (com índice)

Útil quando precisa do **número da posição**.

```java
for (int i = 0; i < nomes.size(); i++) {
    System.out.println("Nome na posição " + i + ": " + nomes.get(i));
}
```

Saída

```java
Nome na posição 0: Ana
Nome na posição 1: João
Nome na posição 2: Maria
```

**Usar quando:** precisa do índice ou quer acessar elementos por posição.

## Iterator

**Iterator** é um objeto que **controla a iteração** sobre a coleção.

Mais controle, permite remover elementos durante a iteração com segurança.

Como funciona

1. Pede o `iterator` da coleção.
2. Usa `hasNext()` para saber se há mais elementos.
3. Usa `next()` para pegar o próximo.

Exemplo, removendo nomes

```java
Iterator<String> it = nomes.iterator();

while (it.hasNext()) {
    String nome = it.next();
    if (nome.length() <= 4) {
        it.remove();  // Remove nomes com 4 letras ou menos
    }
}
System.out.println(nomes);
```

Saída

```java
[Maria]
```

**Usar quando:** precisa remover elementos ou ter mais controle sobre a iteração.

## Iterando `Map` (chave/valor)

Em `Map`, iteramos de forma diferente: usando `entrySet()`.

Exemplo, iterando um map

```java
Map<String, Integer> idades = new HashMap<>();
idades.put("Ana", 25);
idades.put("João", 30);
idades.put("Maria", 28);

for (Map.Entry<String, Integer> entry : idades.entrySet()) {
    System.out.println(entry.getKey() + " tem " + entry.getValue() + " anos");
}
```

Saída

```java
Ana tem 25 anos
João tem 30 anos
Maria tem 28 anos
```

**Usar quando:** quer percorrer tanto a chave quanto o valor.

Além de `entrySet()`, pode iterar só as chaves (`keySet()`) ou só os valores (`values()`), dependendo da necessidade.

Exemplo

```java
for (String chave : idades.keySet()) {
    System.out.println("Chave: " + chave);
}

for (Integer valor : idades.values()) {
    System.out.println("Valor: " + valor);
}
```
