# 🏗️ PIM — Platform Independent Model: Hotel Bela Vista

> **Curso:** Tecnologia em Sistemas para Internet | **Módulo:** 3  
> **Componente Curricular:** Engenharia de Software  
> **Professor:** Gaio B. Oliveira  
> **Atividade:** Semana 05 — Modelagem UML (Perspectivas do Time)  
> **Projeto:** Sistema de Gestão Hoteleira — Hotel Bela Vista

---

## Sumário

1. [Perspectiva de Interação — Diagrama de Sequência](#1-perspectiva-de-interação--diagrama-de-sequência)
2. [Perspectiva Estrutural — Diagrama de Classes](#2-perspectiva-estrutural--diagrama-de-classes)
3. [Perspectiva Comportamental — Diagrama de Estados](#3-perspectiva-comportamental--diagrama-de-estados)

---

## 1. Perspectiva de Interação — Diagrama de Sequência

> **Responsável:** Estudante 1  
> **Escopo:** Processo de check-in do hóspede, desde a consulta de CPF até o alerta de limpeza pós-checkout.

```mermaid
sequenceDiagram
    actor R as Recepcionista
    participant S as Sistema
    participant BD as Banco de Dados
    actor C as Camareira

    R->>S: 1. Informar CPF do hóspede
    S->>BD: 2. Consultar hóspede por CPF
    BD-->>S: 3. Dados do hóspede (ou não encontrado)
    S-->>R: 4. Exibir dados / solicitar cadastro
    R->>S: 5. Selecionar quarto e datas
    S->>BD: 6. Verificar disponibilidade do quarto
    BD-->>S: 7. Quarto disponível
    S->>BD: 8. Registrar reserva (status: Ocupado)
    BD-->>S: 9. Reserva confirmada
    S-->>R: 10. Confirmar check-in + valor da diária

    Note over S,C: Evento disparado após o checkout
    S-->>C: 11. Alerta de limpeza do quarto
    C-->>S: 12. Confirmar limpeza concluída
```

**Decisões de modelagem:**
- A consulta por CPF antes da reserva implementa a regra RF02 (reconhecimento de hóspede recorrente).
- O passo 8 inclui o bloqueio de overbooking, seguindo RF06 — o sistema verifica disponibilidade antes de registrar.
- O alerta de limpeza (passo 11) é um evento assíncrono disparado automaticamente após checkout, atendendo RF12.

---

## 2. Perspectiva Estrutural — Diagrama de Classes

> **Responsável:** Estudante 2  
> **Escopo:** Estrutura estática do sistema — classes, atributos, métodos e relacionamentos.

```mermaid
classDiagram
    class Hospede {
        -int id
        -String nome
        -String cpf
        -String telefone
        +cadastrar() void
        +buscarPorCPF() Hospede
        +atualizar() void
    }

    class Quarto {
        -int id
        -int numero
        -TipoQuarto tipo
        -Decimal precoDiaria
        -StatusQuarto status
        +verificarDisponibilidade() Boolean
        +atualizarStatus() void
    }

    class Reserva {
        -int id
        -Date dataCheckin
        -Date dataCheckout
        -Decimal valorTotal
        +calcularValorTotal() Decimal
        +realizarCheckin() void
        +realizarCheckout() void
        +bloquearOverbooking() Boolean
    }

    class ConsumoExtra {
        -int id
        -String descricao
        -Decimal valor
        -Date dataLancamento
        +lancarItem() void
    }

    class RelatorioMensal {
        -int mes
        -int ano
        -int totalReservas
        -Decimal faturamentoBruto
        +gerar() void
        +exportarPDF() void
    }

    class TipoQuarto {
        <<enumeration>>
        SIMPLES
        LUXO
        FAMILIA
    }

    class StatusQuarto {
        <<enumeration>>
        LIVRE
        OCUPADO
        EM_LIMPEZA
    }

    Hospede "1" --> "N" Reserva : realiza
    Quarto "1" --> "N" Reserva : alocado em
    Reserva "1" *-- "N" ConsumoExtra : contém
    RelatorioMensal ..> Reserva : usa
    Quarto --> TipoQuarto : é do tipo
    Quarto --> StatusQuarto : possui
```

**Decisões de modelagem:**
- A composição (`*--`) entre `Reserva` e `ConsumoExtra` garante que os itens de consumo não existem sem uma reserva (RN03).
- `TipoQuarto` e `StatusQuarto` são enumerações para evitar valores arbitrários e garantir consistência (RN01, RN02).
- O método `bloquearOverbooking()` em `Reserva` encapsula a regra RF06 diretamente na classe responsável.

---

## 3. Perspectiva Comportamental — Diagrama de Estados

> **Responsável:** Estudante 3  
> **Escopo:** Ciclo de vida completo de um quarto — todos os estados possíveis e as transições entre eles.

```mermaid
stateDiagram-v2
    [*] --> Livre : quarto cadastrado

    Livre --> Reservado : reserva confirmada

    Reservado --> Livre : reserva cancelada\n[prazo expirado]
    Reservado --> Ocupado : check-in realizado

    Ocupado --> Ocupado : consumo extra lançado
    Ocupado --> EmLimpeza : checkout concluído\n[conta quitada]
    Ocupado --> Ocupado : checkout negado\n[conta pendente]

    EmLimpeza --> Livre : limpeza confirmada

    EmLimpeza --> [*] : quarto desativado

    state Ocupado {
        [*] --> AguardandoCheckout
        AguardandoCheckout --> AguardandoCheckout : novo item lançado
    }
```

**Decisões de modelagem:**
- A transição `Ocupado → EmLimpeza` só é permitida com a guarda `[conta quitada]`, implementando RN03.
- A transição `EmLimpeza → Livre` só ocorre após confirmação explícita da camareira, implementando RN02.
- O estado `Reservado` tem uma transição de saída para `Livre` por cancelamento, cobrindo o caso de no-show.
- O estado final (`[*]`) representa a desativação permanente do quarto (ex: reforma, remoção do sistema).

---

## Síntese do PIM

| Diagrama | Perspectiva | O que modela |
|---|---|---|
| Sequência | Interação | Como os objetos trocam mensagens durante o check-in |
| Classes | Estrutural | Quais entidades existem, seus dados e responsabilidades |
| Estados | Comportamental | Como o quarto muda de estado ao longo do tempo |

> **Nota:** Este PIM é independente de plataforma — não menciona linguagem de programação, banco de dados específico ou tecnologia de interface. Essas decisões serão tomadas no PSM (Platform Specific Model) na próxima etapa.

---

*📁 Repositório: `semana-09/pim-diagramas-uml.md`*  
*🗓️ Atividade: Modelagem UML — Engenharia de Software*
