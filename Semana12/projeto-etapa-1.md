# SAI – Sistema de Alerta Inteligente

*Projeto Final – Etapa 1*
*Desenvolvimento Ágil com Scrum*

*Instituto Federal de São Paulo – Campus São João da Boa Vista*
Curso: Tecnologia em Sistemas para Internet
Professor: Gaio Belitardo de Oliveira

*Integrantes:*
- Alexandro de Oliveira dos Santos
- André Frigo Lima
- Danilo Rodrigues Alves de Sousa
- Rafael Torres de Araujo
- Victor Emanuel de Souza

São João da Boa Vista – SP, 2026

---

## 1. Visão do Produto

O SAI (Sistema de Alerta Inteligente) é uma plataforma desenvolvida para monitorar áreas de risco e auxiliar órgãos responsáveis na prevenção de situações perigosas, como enchentes, deslizamentos e interrupções em vias urbanas.

O sistema permite o cadastro de áreas críticas, emissão automática de alertas, visualização de informações em tempo real e acompanhamento operacional das ocorrências.

O principal objetivo do projeto é melhorar o tempo de resposta das equipes responsáveis, aumentar a segurança da população e facilitar a tomada de decisões em emergências.

---

## 2. Personas

### Carlos – Operador da Defesa Civil
Responsável pelo monitoramento das áreas de risco e gerenciamento das ocorrências em tempo real. Necessita receber alertas rápidos para agir com eficiência em situações emergenciais.

### Mariana – Administradora do Sistema
Responsável pelo gerenciamento de usuários, permissões e organização das áreas monitoradas dentro da plataforma.

### João – Motorista de Transporte Urbano
Necessita receber informações sobre rotas afetadas para evitar regiões perigosas e garantir maior segurança no trajeto.

---

## 3. Product Backlog Inicial — User Stories

| ID   | User Story |
|------|------------|
| US01 | Como um operador da defesa civil, eu quero visualizar um painel operacional de riscos para acompanhar ocorrências em tempo real. |
| US02 | Como um operador, eu quero receber alertas automáticos de risco para agir rapidamente em situações críticas. |
| US03 | Como um administrador, eu quero cadastrar áreas de risco para organizar os locais monitorados. |
| US04 | Como um operador, eu quero visualizar um mapa interativo para identificar áreas afetadas com facilidade. |
| US05 | Como um motorista, eu quero receber avisos sobre rotas afetadas para evitar regiões perigosas. |
| US06 | Como um administrador, eu quero gerar relatórios operacionais para analisar ocorrências registradas. |
| US07 | Como um cidadão, eu quero receber alertas via WhatsApp ou SMS para me manter informado sobre riscos próximos. |
| US08 | Como um operador, eu quero classificar alertas por gravidade para priorizar atendimentos. |
| US09 | Como um administrador, eu quero controlar usuários e permissões para garantir segurança no sistema. |
| US10 | Como um operador, eu quero consultar o histórico de alertas para acompanhar eventos anteriores. |

---

## 4. Planilha de Priorização

| ID   | Funcionalidade                      | MoSCoW       | Valor (1–5) | Esforço (1–5) | Quadrante                  |
|------|-------------------------------------|--------------|-------------|----------------|----------------------------|
| US01 | Painel operacional de riscos        | Must Have    | 5           | 3              | Grande Projeto             |
| US02 | Alertas automáticos                 | Must Have    | 5           | 2              | Vitória Rápida (Quick Win) |
| US03 | Cadastro de áreas de risco          | Must Have    | 5           | 2              | Vitória Rápida (Quick Win) |
| US04 | Mapa interativo                     | Must Have    | 5           | 3              | Grande Projeto             |
| US05 | Avisos de rotas afetadas            | Should Have  | 4           | 3              | Grande Projeto             |
| US06 | Relatórios operacionais             | Should Have  | 4           | 2              | Vitória Rápida (Quick Win) |
| US07 | Alertas via WhatsApp/SMS            | Should Have  | 5           | 4              | Grande Projeto             |
| US08 | Classificação de alertas por gravidade | Must Have | 5           | 2              | Vitória Rápida (Quick Win) |
| US09 | Controle de usuários e permissões   | Must Have    | 5           | 3              | Grande Projeto             |
| US10 | Histórico de alertas                | Should Have  | 4           | 2              | Vitória Rápida (Quick Win) |

---

## 5. Fila Única – Backlog Ordenado

| Rank | ID   | Funcionalidade                        |
|------|------|---------------------------------------|
| 1°   | US02 | Alertas automáticos de risco          |
| 2°   | US03 | Cadastro de áreas de risco            |
| 3°   | US08 | Classificação de alertas por gravidade |
| 4°   | US01 | Painel operacional de riscos          |
| 5°   | US04 | Mapa interativo de áreas de risco     |
| 6°   | US09 | Controle de usuários e permissões     |
| 7°   | US06 | Relatórios operacionais               |
| 8°   | US10 | Histórico de alertas                  |
| 9°   | US05 | Avisos de rotas afetadas              |
| 10°  | US07 | Alertas via WhatsApp/SMS              |

---

## 6. Considerações Finais

O backlog foi organizado priorizando funcionalidades essenciais para o funcionamento inicial do sistema (MVP), garantindo que as funcionalidades mais críticas sejam desenvolvidas primeiro. A priorização utilizou os métodos MoSCoW e Valor vs. Esforço para maximizar o retorno de negócio e reduzir riscos durante o desenvolvimento ágil.
