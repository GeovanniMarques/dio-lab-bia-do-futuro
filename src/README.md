# Código da Aplicação

Esta pasta contém o código-fonte do agente financeiro **Fin**, desenvolvido para o Bootcamp Bradesco GenAI & Dados.

## Estrutura do Projeto

O projeto foi organizado para separar a interface da lógica da inteligência artificial:

```text
src/
├── app.py              # Interface do usuário (Streamlit)
├── agente.py           # Cérebro da Fin (Lógica de integração com a LLM)
├── config.py           # Gerenciamento de chaves de API e variáveis de ambiente
└── requirements.txt    # Lista de bibliotecas necessárias
```

## Descrição dos Arquivos
- **app.py**: Gerencia a interface visual do chat, exibe as mensagens do João Silva e as respostas da Fin, e carrega os dados dos CSVs/JSONs.
- **agente.py**: Contém a função que envia o prompt (criado na Etapa 3) para a API da OpenAI/Gemini e retorna a resposta formatada.
- **config.py**: Utiliza a biblioteca python-dotenv para carregar sua chave de API de forma segura a partir de um arquivo .env.


## Exemplo de requirements.txt

```
streamlit
openai
pandas
python-dotenv
```

## Como Rodar

Siga os passos abaixo no seu terminal (VS Code) para configurar e executar o projeto localmente:

### 1. Clonar o Repositório
Se ainda não o fez, clone seu fork para sua máquina:
```bash
git clone [https://github.com/GeovanniMarques/dio-lab-bia-do-futuro.git](https://github.com/GeovanniMarques/dio-lab-bia-do-futuro.git)
cd dio-lab-bia-do-futuro
```

### 2. Criar um Ambiente Virtual
É uma boa prática para manter as bibliotecas do projeto isoladas:
```bash
# Criar o ambiente
python -m venv venv

# Ativar o ambiente
# No Windows:
venv\Scripts\activate
# No Linux/Mac:
source venv/bin/activate
```

### 3. Instalar Dependências
Instale todas as bibliotecas listadas no arquivo ``requirements.txt``:
```bash
pip install -r src/requirements.txt
```

### 4. Configurar Variáveis de Ambiente
Crie um arquivo chamado .env na raiz do projeto e adicione sua chave da API:
```
OPENAI_API_KEY=seu_token_aqui
```

### 5. Executar a Aplicação
Inicie o servidor do Streamlit:
```bash
streamlit run src/app.py
```
