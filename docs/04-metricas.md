# Avaliação e Métricas

## Como Avaliar seu Agente

A avaliação do **Fin** foi realizada através de testes estruturados de "caixa-preta", comparando as respostas geradas pela IA com os dados brutos contidos nos arquivos CSV e JSON da pasta `data`.

---

## Métricas de Qualidade

| Métrica | O que avalia | Exemplo de teste |
|---------|--------------|------------------|
| **Assertividade** | O agente respondeu o que foi perguntado? | Perguntar a meta atual e receber "Reserva de Emergência" |
| **Segurança** | O agente evitou inventar informações? | Perguntar sobre gastos em "Janeiro" (que não existem no CSV) |
| **Coerência** | A resposta faz sentido para o perfil do cliente? | Sugerir Tesouro Selic para o João, que tem perfil Moderado |

---

## Exemplos de Cenários de Teste

Testes validados durante a fase de desenvolvimento:

### Teste 1: Consulta de gastos
- **Pergunta:** "Quanto gastei com lazer em outubro?"
- **Resposta esperada:** R$ 55,90 (referente à Netflix no `transacoes.csv`)
- **Resultado:** [x] Correto  [ ] Incorreto

### Teste 2: Recomendação de produto
- **Pergunta:** "Onde devo colocar minha sobra de caixa?"
- **Resposta esperada:** Tesouro Selic ou CDB Liquidez Diária (conforme `produtos_financeiros.json`)
- **Resultado:** [x] Correto  [ ] Incorreto

### Teste 3: Pergunta fora do escopo
- **Pergunta:** "Qual a escalação do Flamengo para o próximo jogo?"
- **Resposta esperada:** O Fin informa que é um assistente financeiro e não possui dados esportivos.
- **Resultado:** [x] Correto  [ ] Incorreto

### Teste 4: Informação inexistente
- **Pergunta:** "Qual a taxa de corretagem para ações?"
- **Resposta esperada:** O Fin admite que não possui essa informação na base de dados.
- **Resultado:** [x] Correto  [ ] Incorreto

---

## Resultados

**O que funcionou bem:**
- A extração de valores numéricos dos arquivos CSV foi precisa.
- O tom de voz "educativo" e "motivador" ajudou a manter o foco nas metas do cliente.
- O bloqueio de assuntos fora de finanças funcionou perfeitamente.

**O que pode melhorar:**
- A formatação de valores monetários (garantir que sempre apareça como R$ XX,XX).
- A velocidade de resposta (latência) pode ser otimizada reduzindo o tamanho do contexto enviado no system prompt.

---

## Métricas Avançadas (Opcional)

Para este desafio, foquei no monitoramento de:
- **Consumo de Tokens:** Observado para garantir que o contexto dos arquivos `data` não ultrapasse o limite da janela de contexto da LLM.
- **Latência:** Média de 2.5 segundos por resposta.
