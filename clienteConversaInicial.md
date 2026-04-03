# Documentação de Requisitos - Hotel Bela Vista

**Cliente:** Sr. Geraldo (Proprietário)
**Analista:** [Danilo]
**Data:** 02/04/2026

## 1. Histórias de Usuário (User Stories)

| ID | Usuário | Desejo (O que eu quero) | Prioridade |
|:---:|:---:|:---:|:---:|
| US01 | Proprietário | Ver um mapa visual dos quartos (livre, ocupado, limpeza) para gerir a ocupação rapidamente. | Alta |
| US02 | Proprietário | Cadastrar hóspedes com Nome, CPF e Telefone para manter um histórico de contatos. | Alta |
| US03 | Proprietário | Registrar o tipo de quarto (Simples, Luxo, Família) com seus respectivos preços automáticos. | Alta |
| US04 | Proprietário | Lançar despesas extras (frigobar/lanches) na conta do hóspede durante a estadia. | Média |
| US05 | Proprietário | Visualizar um relatório de lucros mensais sem necessidade de cálculos manuais. | Alta |
| US06 | Camareira/Admin | Receber alertas/avisos de quais quartos precisam de limpeza após o checkout. | Média |

---

## 2. Requisitos do Sistema

### 2.1 Requisitos Funcionais (RF)
* **RF01:** O sistema deve permitir o cadastro de hóspedes (Nome, CPF, Telefone).
* **RF02:** O sistema deve permitir a reserva de quartos, impedindo que dois hóspedes ocupem o mesmo quarto no mesmo período (Bloqueio de Overbooking).
* **RF03:** O sistema deve fornecer uma interface visual (Mapa de Ocupação) com status dos quartos.
* **RF04:** O sistema deve calcular automaticamente o valor da hospedagem com base no tipo de quarto e dias de estadia.
* **RF05:** O sistema deve permitir a inserção de itens de consumo na conta do hóspede em tempo real.
* **RF06:** O sistema deve gerar um relatório financeiro de faturamento e lucro mensal.

### 2.2 Requisitos Não Funcionais (RNF)
* **RNF01 (Usabilidade):** A interface deve ser extremamente simples e intuitiva, adequada para usuários com zero conhecimento técnico.
* **RNF02 (Confiabilidade):** O sistema deve garantir a persistência dos dados (as informações não podem "sumir").
* **RNF03 (Performance):** O processo de check-in deve ser ágil para reduzir filas na recepção.

---

## 3. Regras de Negócio (RN)
* **RN01:** O preço da diária é definido pela categoria do quarto: Simples, Suíte Luxo ou Quarto Família.
* **RN02:** Um quarto só pode ser marcado como "Livre" após a confirmação da limpeza.
* **RN03:** O checkout só poderá ser finalizado após o fechamento da conta de consumo extra.
