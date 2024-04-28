# Desafio-Tech-Pottencial-Payment-API

Sobre o conceito de **Payment API** (API de Pagamentos).

Uma **Payment API** é uma interface de programação de aplicativos que permite a integração de funcionalidades de pagamento em sistemas de software. Ela é projetada para facilitar transações seguras entre compradores e vendedores, processando pagamentos, gerenciando autorizações de pagamento e mantendo a segurança dos dados do cartão.

### Características Principais:
- **Segurança**: Utiliza padrões de segurança como SSL/TLS e PCI DSS para proteger as informações de pagamento.
- **Integração**: Pode ser integrada a diversas plataformas de e-commerce, sistemas de gestão ou aplicativos móveis.
- **Flexibilidade**: Suporta diferentes métodos de pagamento, como cartões de crédito, débito, transferências bancárias e carteiras digitais.
- **Automatização**: Permite a automatização do processo de cobrança, reduzindo erros manuais e aumentando a eficiência.

### Funcionalidades Típicas:
1. **Processamento de Pagamentos**: Autoriza e processa transações de pagamento em tempo real.
2. **Gerenciamento de Transações**: Permite visualizar, pesquisar e reembolsar transações.
3. **Autenticação e Autorização**: Verifica a identidade do pagador e autoriza a transação.
4. **Relatórios e Análises**: Fornece relatórios detalhados sobre as transações para análise financeira.

### Exemplo de Uso em Código:
```csharp
// Exemplo de um endpoint para processar pagamentos usando uma Payment API em .NET Core
[HttpPost("processar-pagamento")]
public IActionResult ProcessarPagamento([FromBody] DadosPagamento pagamento)
{
    var resultado = PaymentService.ProcessarPagamento(pagamento);
    if (resultado.Sucesso)
    {
        return Ok(resultado.TransacaoId);
    }
    else
    {
        return BadRequest(resultado.MensagemErro);
    }
}

public class DadosPagamento
{
    public string NumeroCartao { get; set; }
    public string Validade { get; set; }
    public string CVV { get; set; }
    public decimal Valor { get; set; }
}
```

Neste exemplo, o método `ProcessarPagamento` recebe os dados de pagamento e utiliza um serviço de pagamento para processar a transação. Se bem-sucedido, retorna o ID da transação; caso contrário, retorna uma mensagem de erro.

As **Payment APIs** são essenciais para o comércio eletrônico moderno, proporcionando uma experiência de pagamento suave e segura para os usuários. Se você estiver construindo uma API de pagamentos como parte de um desafio técnico, é importante considerar todos esses aspectos para garantir que sua implementação seja robusta e segura. 

Sobre o desafio do projeto da API de Pagamentos. Vamos dividir isso em módulos e dar exemplos práticos.

### Módulo 1: Configuração Inicial
- **Fork do Projeto**: Crie um fork do repositório fornecido no GitLab e adicione `@Pottencial` como membro.
- **Commits**: Faça commits vazios no início e no final do teste, e após cada ciclo de refatoração.

### Módulo 2: Construção da API
- **Tecnologia**: Escolha entre .Net Core, Java ou NodeJs com Typescript para construir a API REST.
- **Documentação Swagger**: Exponha uma rota `/api-docs` para a documentação da API.

### Módulo 3: Operações da API
1. **Registrar Venda**:
   - Endpoint: `POST /vendas`
   - Corpo da Requisição: Dados do vendedor e itens vendidos.
   - Ação: Registra a venda com status "Aguardando pagamento".

2. **Buscar Venda**:
   - Endpoint: `GET /vendas/{id}`
   - Ação: Retorna os detalhes da venda com base no ID fornecido.

3. **Atualizar Venda**:
   - Endpoint: `PUT /vendas/{id}`
   - Corpo da Requisição: Novo status da venda.
   - Ação: Atualiza o status da venda conforme as transições permitidas.

### Módulo 4: Regras de Negócio
- **Dados da Venda**: Informações do vendedor, data, ID do pedido e itens vendidos.
- **Dados do Vendedor**: ID, CPF, nome, e-mail e telefone.
- **Transições de Status**: Defina as transições de status permitidas para a venda.

### Módulo 5: Avaliação
- **Arquitetura**: Estruture o projeto considerando camadas e responsabilidades.
- **Orientação a Objetos**: Aplique conceitos de OOP.
- **Boas Práticas**: Siga princípios como SOLID, DRY, KISS e, opcionalmente, DDD.
- **Testes Unitários**: Escreva testes para validar sua solução.
- **Padrão REST**: Garanta que a API siga o padrão REST.

### Exemplo Prático: Registrar Venda
```json
POST /vendas
{
  "vendedor": {
    "id": "vendedor123",
    "cpf": "123.456.789-00",
    "nome": "João Silva",
    "email": "joao.silva@email.com",
    "telefone": "(31) 98765-4321"
  },
  "itensVendidos": [
    {
      "produtoId": "prod001",
      "quantidade": 2,
      "preco": 150.00
    }
  ]
}
```

Resposta esperada: `201 Created` com o corpo da venda registrada, incluindo o status "Aguardando pagamento".

Lembre-se de que a criatividade e a aplicação dos conhecimentos adquiridos são essenciais.
