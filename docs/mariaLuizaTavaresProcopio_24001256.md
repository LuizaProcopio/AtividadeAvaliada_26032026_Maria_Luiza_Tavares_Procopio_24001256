# Avaliação — Engenharia de Software
**Sistema Integrado de Gestão de Farmácia — MVP De Processo de Vendas Integrado com o Estoque e Contas em Aberto**

Aluno: *Maria Luiza Tavares Procopio*  
RA: *24001256*  
Data: *26/03/2026*  

---

# 1. Definição do MVP
O MVP abrange o fluxo de vendas na farmácia desde a identificação do cliente até o a finalização da compra.
Integrando também o estoque da farmacia ao sistema, permitindo atualização rápida na entrada de mercadoria quanto também para venda, 
além e um registro de quais são as contas em aberto e contas a receber.

dentro do MVP: 
- identificação de usuario.
  
- cadastro de cliente.
  
- busca de mercadoria e cliente.
  
- verificação de estoque.
  
- registro de estoque.
  
- registro de vendas, emissão de comprovante, NF.
  
- registro de contas a receber.

Fora do MVP:
- contas a pagar.
  
- gestão finaceira.
  
- adiministração de usuarios e permissões.
  
- gestão completa de vendas.
  
- compras e fornecedores.

Justificativa:
Essa escollha torna mais o desenvolvimento mais eficiente, pois une operações de vendas, controle de estoque.
Como o setor de vendas move as mercadorias, essa área esta conectada perfeitamente ao estoque.

---

# 2. Regras de Negócio 

**RN01 —**  Mercadoria sem estoque não pode ser vendida.

**RN02 —**  Clientes sem cadastro devem ser registrados antes de ser possivel registrar a venda.

**RN03 —**  O estoque deve ser atualizado logo após a finalização de uma venda.

**RN04 —**  O sistema deve recusar alterações de preço feitas por usuarios não autorizados.

**RN05 —**  Vendas feitas a prazo deve gerar um registro de contas a receber.

---

# 3. Requisitos Funcionais

**RF01 —**  Registo de vendas feitas a prazo e que estão a receber.

**RF02 —**  atualizar o estoque após uma venda.

**RF03 —**  finalizar venda e gerar comprovante de operação.

**RF04 —**  permitir de alterar estoque.

**RF05 —**  permitir de visualização de estoque ou consulta de produtos.

**RF06 —**  permitir pesquisar um produto ao escrever seu nome, código de barra.

**RF07 —**  permitir cadastro de novo cliente.

**RF08 —**  permitir busca de cliente por nome, telefone ou documento pessoal.

---

# 🛡 4. Requisitos Não Funcionais

**RNF01 —**  As permissões de vendas devem ser permitidas aos farmacêuticos.

**RNF02 —**  o sistema deve ter uma tela acessível com telas responsivas.

**RNF03 —**  dados dos clientes e do estoque devem ser armazenados de forma segura.

**RNF04 —**  O sistema deve registrar as ações feitas pelos usuários, erros e tentativas de acesso.


---

# 5. Casos de Uso 

<img width="449" height="891" alt="image" src="https://github.com/user-attachments/assets/641d4f27-67aa-41f1-a2be-69163c660b21" />

<img width="392" height="1264" alt="image" src="https://github.com/user-attachments/assets/d3eb307c-7baf-4c6e-9f2f-2a92375091fc" />

---

# 6. Documentação dos Casos de Uso
---

## **UC01 — Realizar Login**
**Ator(es): Funcionario**  
**Descrição: Permite que o usuario se conecte ao sistema**  
**Pré-condições: o usuario deve ter cadastro no sistema**  
**Pós-condições: sessão iniciada**  

### Fluxo Principal
1.  usuario informa informações de acesso (nome de usuário e senha)
2.  o sistema varifica esses dados e valida credenciais
3.  sistema libera acesso a tela principal da aplicação

### Fluxos Alternativos / Exceções
- FA01 —  Credenciais inválidas: sistema exibe mensagem de erro.
- FA02 —  Usuário inativo: acesso negado.

### Relacionamentos
- **Include:** -  
- **Extend:** - 

---

## **UC02 — Cadadastro de cliente**
**Ator(es): Funcionario**  
**Descrição: Permite que o registro um novo cliente no sistema.**  
**Pré-condições: Estar logado**  
**Pós-condições: Cliente salvo no banco de dados.**  

### Fluxo Principal
1.  Funcionário acessa "Cadastrar Cliente".
2.  Preenche nome, documento, telefone e endereço.
3.  Sistema valida dados.
4.  Sistema confirma o cadastro.

### Fluxos Alternativos / Exceções
- FA01 —  Dados incompletos: sistema solicita correção.
- FA02 —  Cliente já existe: sistema apresenta o cadastro existente.

### Relacionamentos
- **Include:** -  
- **Extend:** - Extend: UC08 (Buscar Cliente)

---


## **UC03 — Buscar Cliente**
**Ator(es): Funcionario**  
**Descrição: Permite pesquisa por nome, telefone ou documento.**  
**Pré-condições: Estar logado.**  
**Pós-condições: Sistema exibe resultados encontrados.**  

### Fluxo Principal
1.  Funcionário insere parâmetro de busca.
2.  Sistema pesquisa no banco.
3.  Sistema exibe cliente(s) correspondentes.

### Fluxos Alternativos / Exceções
- FA01 —  Cliente não encontrado: exibir aviso.

### Relacionamentos
- **Include:** -  
- **Extend:** - UC02 (Cadastro de Cliente)

---

## **UC04 — **
**Ator(es): Funcionario**  
**Descrição: Pesquisar produto por nome ou código de barras.**  
**Pré-condições: Estar logado.**  
**Pós-condições: Produto exibido para consulta.**  

### Fluxo Principal
1.  Funcionário busca produto por nome ou código
2.  Sistema consulta inventário.
3.  Sistema exibe dados do produto.

### Fluxos Alternativos / Exceções
- FA01 —  Produto não encontrado.

### Relacionamentos
- **Include:** -  
- **Extend:** -

---

## **UC05 — Atualizar Estoque**
**Ator(es): Funcionário autorizado**  
**Descrição: Permite entrada e ajuste de estoque.**  
**Pré-condições: Permissão concedida**  
**Pós-condições: Quantidade atualizada**  

### Fluxo Principal
1.  Funcionário seleciona produto.
2.  Informa novo valor/entrada.
3.  Sistema atualiza o estoque.
4.  Confirma operação.

### Fluxos Alternativos / Exceções
- FA01 —  Usuário sem permissão.
- FA02 —  Informações inválidas.

### Relacionamentos
- **Include:** -  UC04 (Buscar Produto)
- **Extend:** -

---

## **UC06 — Verificar Estoque Antes da Venda**
**Ator(es): Sistema**  
**Descrição: Sistema confirma que há produto suficiente para vender**  
**Pré-condições: Produto buscado.**  
**Pós-condições: Venda pode (ou não) continuar.**  

### Fluxo Principal
1.  Sistema verifica quantidade disponível.
2.  Se houver estoque, libera venda.

### Fluxos Alternativos / Exceções
- FA01 —  Estoque insuficiente → recusar venda.

### Relacionamentos
- **Include:** -  UC04
- **Extend:** - UC07 (Registrar Venda)

---

## **UC07 — Registrar Venda**
**Ator(es): Funcionario**  
**Descrição: Registra venda à vista ou a prazo.**  
**Pré-condições: Estoque disponível.**  
**Pós-condições: Venda concluída.**  

### Fluxo Principal
1.  Funcionário seleciona cliente.
2.  Adiciona produtos.
3.  Sistema confirma estoque.
4.  Funcionário escolhe forma de pagamento.
5.  Sistema registra venda.
6.  Sistema gera comprovante/NF.

   
### Fluxos Alternativos / Exceções
- FA01 —  Estoque insuficiente.
- FA02 —  Cliente não encontrado.
- FA03 —  Pagamento recusado.

### Relacionamentos
- **Include:** -  UC03, UC04, UC06
- **Extend:** - UC09 (Registrar Conta a Receber)

---

## **UC08 — Emitir Comprovante / Nota Fiscal**
**Ator(es): Sistema**  
**Descrição: Gera comprovante e/ou NF.**  
**Pré-condições: Venda registrada.**  
**Pós-condições: Documento emitido.**  

### Fluxo Principal
1.  Sistema coleta dados da venda.
2.  Sistema gera arquivo/documento.
3.  Exibe ao usuário.

### Fluxos Alternativos / Exceções
- FA01 —  Falha de geração.

### Relacionamentos
- **Include:** -  
- **Extend:** -

---

## **UC09 — *Registrar Conta a Receber*
**Ator(es): Sistema**  
**Descrição: Permite que o sistema registre clientes que pagam depois.**  
**Pré-condições: venda no modo a prazo**  
**Pós-condições: criado débito em aberto.**  

### Fluxo Principal
1.  sistema reconhece venda a prazo.
2.  o sistema cria registro de conta a receber.
3.  salva no financeiro.

### Fluxos Alternativos / Exceções
- FA01 —  Falha ao registrar.

### Relacionamentos
- **Include:** -  
- **Extend:** -

---

## **UC10 — Consultar Contas em Aberto**
**Ator(es): Funcionario**  
**Descrição: Exibe dívidas pendentes**  
**Pré-condições: estar conectado ao sistema**  
**Pós-condições: lista de dividas exibida**  

### Fluxo Principal
1.  Funcionário acessa menu de contas.
2.  Sistema lista clientes devedores.
3.  Funcionário pode filtrar por nome, valor, vencimento.

### Fluxos Alternativos / Exceções
- FA01 —  Nenhuma conta encontrada.

### Relacionamentos
- **Include:** -  
- **Extend:** -

---
## UC01 — *Realizar Login*
<img width="263" height="312" alt="image" src="https://github.com/user-attachments/assets/ad30e78e-03b2-42de-960e-15c5dd8111af" />

## UC02 — *Cadastrar Cliente*
<img width="243" height="367" alt="image" src="https://github.com/user-attachments/assets/09ade3b9-d1c4-4f99-a2b0-f7cfc768daf5" />

## UC03 — *Buscar Cliente*
<img width="310" height="312" alt="image" src="https://github.com/user-attachments/assets/88706808-bbb7-4bc7-b8d2-681470233e29" />

## UC04 — *Buscar Produto*
<img width="231" height="312" alt="image" src="https://github.com/user-attachments/assets/b22cd339-cedc-4365-bcf2-a484254f413f" />

## UC05 — *Atualizar Estoque*
<img width="231" height="367" alt="image" src="https://github.com/user-attachments/assets/d244dc26-7727-4b8e-b8e9-ee45c4d8b657" />

## UC06 — *Verificar Estoque Antes da Venda*
<img width="247" height="257" alt="image" src="https://github.com/user-attachments/assets/0e1a7a11-2299-479d-baaf-37c4fd454d96" />

## UC07 — *Registrar Venda*
<img width="477" height="541" alt="image" src="https://github.com/user-attachments/assets/40a136db-3e0b-41c6-8a2f-f0c87c27f37a" />

## UC08 — *Emitir Comprovante / Nota Fiscal*
<img width="241" height="312" alt="image" src="https://github.com/user-attachments/assets/7f75953c-d39b-4ea1-9799-0d4843d841b7" />

## **UC09 — *Registrar Conta a Receber*
<img width="192" height="312" alt="image" src="https://github.com/user-attachments/assets/40ec5b43-15dd-43f9-9d49-46d66cbcc6d6" />

## UC10 — *Consultar Contas em Aberto*
<img width="246" height="312" alt="image" src="https://github.com/user-attachments/assets/4df515df-de86-46ef-9895-f87fd9dcb12c" />


---
