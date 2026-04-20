# Base de Conhecimento

## Dados Utilizados

O agente utiliza os arquivos da pasta `data` para criar uma experiência personalizada e fundamentada em dados reais do cliente fictício.

| Arquivo | Formato | Utilização no Agente |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Utilizado para manter a continuidade do suporte e evitar repetições de temas já resolvidos (como dúvidas sobre CDB/Selic). |
| `perfil_investidor.json` | JSON | Crucial para entender as metas do João Silva (ex: reserva de emergência e entrada do apartamento) e o nível de risco aceito. |
| `produtos_financeiros.json` | JSON | Serve como o "catálogo" de soluções que a Bia pode sugerir quando o usuário tem sobra de caixa no mês. |
| `transacoes.csv` | CSV | A base principal para a análise de economia, onde a Bia identifica gastos com lazer e transporte para sugerir otimizações. |

> [!TIP]
> **Quer um dataset mais robusto?** Você pode utilizar datasets públicos do [Hugging Face](https://huggingface.co/datasets) relacionados a finanças, desde que sejam adequados ao contexto do desafio.

---

## Adaptações nos Dados

Os dados foram mantidos conforme o repositório original para garantir a compatibilidade com os scripts de carregamento, porém, o agente foi instruído a dar **prioridade interpretativa** ao arquivo `transacoes.csv` para realizar o cálculo de "Sobra Mensal" (Receita - Despesas) em tempo real.

---

## Estratégia de Integração

### Como os dados são carregados?
Os arquivos são carregados utilizando a biblioteca `pandas` (para os CSVs) e o módulo `json` do Python no início da execução da aplicação Streamlit. Eles são convertidos para strings formatadas ou dicionários que o LLM consegue processar.

### Como os dados são usados no prompt?
Os dados são injetados dinamicamente no **Contexto do Usuário**. Sempre que o cliente faz uma pergunta, o "Orquestrador" anexa o perfil do investidor e o resumo das transações ao prompt, garantindo que a resposta da Bia não seja genérica, mas sim baseada nos números reais do João Silva.

---

## Exemplo de Contexto Montado

Para garantir a precisão, os dados são passados para a LLM no seguinte formato:

```text
[CONTEXTO FINANCEIRO DO CLIENTE]
Cliente: João Silva (32 anos, Analista de Sistemas)
Perfil: Moderado | Renda Mensal: R$ 5.000,00
Meta Atual: Completar reserva de emergência (Faltam R$ 5.000,00)

RESUMO DE TRANSAÇÕES (OUTUBRO/2025):
- Receita: R$ 5.000,00 (Salário)
- Moradia: R$ 1.380,00 (Aluguel + Luz)
- Lazer/Transporte: R$ 350,90 (Netflix + Uber + Combustível)
- Saúde: R$ 188,00 (Farmácia + Academia)

PRODUTOS DISPONÍVEIS PARA RECOMENDAÇÃO:
- Tesouro Selic (Baixo risco, indicado para Reserva de Emergência)
- CDB Liquidez Diária (102% do CDI)
