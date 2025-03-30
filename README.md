# Desafio de Lógica de Programação Implementado

A classe [GerenciadorEstoque.cs](https://github.com/ErickGabrielS/Teste_Developer/blob/master/TesteDeveloper/GerenciadorEstoque.cs) foi atualizada com a implementação dos métodos pendentes. Veja abaixo a descrição e a funcionalidade de cada um:

## Implementações realizadas:

### [GetSaldo(string referencia)](https://github.com/ErickGabrielS/Teste_Developer/blob/master/TesteDeveloper/GerenciadorEstoque.cs#L41)
Este método retorna o saldo de estoque de uma referência específica.
```csharp
        /// <summary>
        /// Buscar saldo de estoque da referência
        /// </summary>
        /// <param name="referencia">Identificador da referência/produto</param>
        /// <returns>Saldo de estoque</returns>
        public int GetSaldo(string referencia)
        {
            var produto = _estoques.FirstOrDefault(e => e.Referencia == referencia);
            return produto?.SaldoEstoque ?? 0;
        }
```

### [EstoqueDisponivel(string referencia, int quantidadeRequerida)](https://github.com/ErickGabrielS/Teste_Developer/blob/master/TesteDeveloper/GerenciadorEstoque.cs#L30)
Este método verifica se há estoque suficiente para atender à quantidade requerida de uma referência.
```csharp
        /// <summary>
        /// Verifica se a quantidade requerida existe no estoque da referência
        /// </summary>
        /// <param name="referencia">Identificador da referência/produto</param>
        /// <param name="quantidadeRequerida">Quantidade requerida</param>
        /// <returns>Indica se a quantidade requerida existe ou não no estoque</returns>
        public bool EstoqueDisponivel(string referencia, int quantidadeRequerida)
        {
            var produto = _estoques.FirstOrDefault(e => e.Referencia == referencia);
            return produto != null && produto.SaldoEstoque >= quantidadeRequerida;
        }
```

### [ToString()](https://github.com/ErickGabrielS/Teste_Developer/blob/master/TesteDeveloper/GerenciadorEstoque.cs#L56)
Este método retorna uma string formatada com o extrato do estoque, listando todas as referências e seus saldos.
```csharp
        /// <summary>
        /// Gera string com os estoques no formato [Referência: {Referencia} Saldo: {SaldoEstoque}] com uma linha para cada referência
        /// Ex:
        /// Referência: A345 Saldo: 98
        /// Referência: B456 Saldo: 15
        /// </summary>
        /// <returns>String formatada</returns>
        public override string ToString()
        {
            return string.Join("\n", _estoques.Select(e => $"Referência: {e.Referencia} Saldo: {e.SaldoEstoque}"));
        }
```

---

### Tecnologias utilizadas
A implementação foi feita em **C#**, utilizando **.NET Core 3.1**.
Para executar o projeto, certifique-se de ter o [.NET Core SDK 3.1](https://dotnet.microsoft.com/download) instalado em sua máquina.

