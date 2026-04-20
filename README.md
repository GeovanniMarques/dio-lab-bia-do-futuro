# Fin - Mentora de Economia Inteligente 🚀

![Status do Projeto](https://img.shields.io/badge/Status-Em%20Desenvolvimento-blue)
![Bootcamp](https://img.shields.io/badge/Bootcamp-Bradesco%20%26%20DIO-red)

A **Fin** é um agente de inteligência artificial generativa desenvolvido como projeto final do Bootcamp **Bradesco - Java Cloud Native** em parceria com a **DIO**. O objetivo é transformar a gestão financeira pessoal em uma experiência educativa e proativa.

---

## 📌 Índice
1. [Visão Geral](#visão-geral)
2. [Documentação do Agente](#documentação-do-agente)
3. [Base de Conhecimento](#base-de-conhecimento)
4. [Estratégia de Prompts](#estratégia-de-prompts)
5. [Como Executar](#como-executar)
6. [Avaliação e Métricas](#avaliação-e-métricas)
7. [Pitch](#pitch)

---

## 📺 Visão Geral
Muitas pessoas têm dificuldade em interpretar seus gastos e planejar o futuro. A **Fin** atua como uma mentora que "lê" a realidade financeira do usuário (via CSV/JSON) e oferece conselhos personalizados, focando sempre na criação de uma reserva de emergência e educação financeira.

---

## 📑 Documentação do Agente
O agente foi desenhado com uma persona consultiva e acessível.
- **Nome:** Fin
- **Objetivo:** Analisar gastos e sugerir otimizações de orçamento.
- **Persona:** Educativa, encorajadora e focada em segurança.

> [Confira a documentação completa aqui](./docs/01-documentacao-agente.md)

---

## 📂 Base de Conhecimento
A Fin utiliza dados estruturados para garantir que suas respostas sejam baseadas em fatos, evitando alucinações:
- `transacoes.csv`: Histórico de consumo do cliente.
- `perfil_investidor.json`: Metas e tolerância a risco.
- `produtos_financeiros.json`: Opções de investimento em renda fixa.

> [Veja os detalhes da integração de dados](./docs/02-base-conhecimento.md)

---

## 🧠 Estratégia de Prompts
Utilizamos técnicas de **Grounding** e **Few-Shot Prompting** para garantir que a Fin:
1. Nunca invente dados financeiros.
2. Saiba lidar com perguntas fora de escopo.
3. Mantenha o tom de voz "Fin".

> [Acesse o guia de prompts](./docs/03-prompts.md)

---

## 🛠️ Como Executar

### Pré-requisitos
- Python 3.10 ou superior
- Chave de API (OpenAI ou similar)

### Passo a Passo
```bash
# Clone o repositório
git clone [https://github.com/GeovanniMarques/dio-lab-bia-do-futuro.git](https://github.com/GeovanniMarques/dio-lab-bia-do-futuro.git)

# Instale as dependências
pip install -r src/requirements.txt

# Configure sua chave no arquivo .env
OPENAI_API_KEY=seu_token_aqui

# Rode a aplicação
streamlit run src/app.py
```

## 📊 Avaliação e Métricas

A eficácia do agente **Fin** foi validada através de uma série de testes estruturados, garantindo que a inteligência artificial opere dentro dos limites de segurança e precisão técnica exigidos para o setor financeiro.

### Cenários de Teste e Resultados
| ID | Cenário de Teste | Resultado Esperado | Status |
|----|------------------|-------------------|--------|
| 01 | Cálculo de Sobra Mensal | Subtrair despesas (CSV) da renda (JSON) corretamente. | ✅ Passou |
| 02 | Bloqueio de Escopo | Recusar perguntas não financeiras (ex: previsão do tempo). | ✅ Passou |
| 03 | Recomendação Conservadora | Sugerir apenas Renda Fixa para o perfil moderado do João. | ✅ Passou |
| 04 | Prevenção de Alucinação | Admitir ignorância sobre dados não presentes na base. | ✅ Passou |

### Conclusões de Qualidade
- **Assertividade:** O agente demonstrou alta precisão ao extrair dados dos arquivos CSV/JSON.
- **Segurança:** As travas de persona impediram a recomendação de ativos de alto risco, mantendo o foco educativo.
- **Melhoria Contínua:** Identificou-se que a latência pode ser reduzida otimizando o tamanho do contexto enviado para a LLM.

---

## 📢 Pitch

### 1. O Problema
Muitos brasileiros enfrentam dificuldades em interpretar seus hábitos de consumo e planejar o futuro financeiro devido ao "economês" técnico e à complexidade das planilhas bancárias. O João Silva, nosso cliente fictício, possui renda estável, mas não visualiza como atingir sua meta de reserva de emergência.

### 2. A Solução
A **Fin** é uma mentora financeira baseada em IA Generativa que humaniza os dados bancários. Ela analisa as transações reais e o perfil do investidor para oferecer conselhos proativos e educativos, transformando tabelas frias em conversas motivadoras voltadas para objetivos reais.

### 3. Diferencial e Impacto
O grande diferencial da **Fin** é a integração direta com bases de conhecimento personalizadas, garantindo respostas sem alucinações. O impacto social reside na democratização da literacia financeira, auxiliando o cidadão a tomar decisões seguras e conscientes.

---

## 🤝 Contribuição

Este projeto foi desenvolvido como parte do **Bootcamp Bradesco GenAI & Dados**, ministrado pela **DIO**.

- **Desenvolvedor:** [Geovanni Marques](https://github.com/GeovanniMarques)
- **Tecnologias:** Python, Streamlit, Pandas e OpenAI/Gemini API.
- **Objetivo:** Aplicar conceitos de Engenharia de Prompts e RAG (Retrieval-Augmented Generation) em um cenário real de suporte financeiro.

Sinta-se à vontade para abrir uma *issue* ou enviar um *pull request* com sugestões de melhorias!
