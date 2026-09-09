# 📊 Sistema de Sincronização, Validação e Automação de Dados (Google Sheets ↔ Excel)

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Google Sheets API](https://img.shields.io/badge/Google%20Sheets%20API-34A853?style=for-the-badge&logo=googlesheets&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![OpenPyXL](https://img.shields.io/badge/OpenPyXL-GREEN?style=for-the-badge)
![Tkinter](https://img.shields.io/badge/Tkinter-GUI-blue?style=for-the-badge)

Aplicação desktop desenvolvida em Python para automatizar a extração de dados brutos na nuvem via **Google Sheets API**, aplicar regras estritas de sanitização/validação cadastral e gerar relatórios formatados localmente no Excel.

---

## 🎯 O Problema

O processo de coleta descentralizada de dados (formulários, e-mails ou mensagens) gera gargalos operacionais relevantes nas equipes de atendimento e administração:
- **Trabalho manual e repetitivo:** Operadores gastam horas copiando respostas da nuvem para colar em planilhas internas.
- **Erros de digitação e inconsistências:** CPFs digitados incorretamente, números de telefone sem DDD ou sem formatação padrão.
- **Gargalo na triagem:** A falta de uma verificação em tempo real faz com que dados inválidos cheguem à base de produção ou sistemas finais.

---

## 🚀 Como a Ferramenta Resolve Isso

A aplicação conecta a API do Google Sheets à planilha local em poucos segundos com automação ponta a ponta:

1. **Integração em Nuvem com a Google Sheets API (Nível Avançado):** 
   Utilizando autenticação segura por **Conta de Serviço (Service Account)** do Google Cloud, a aplicação acessa a nuvem diretamente via código em segundo plano, consumindo as respostas do formulário em tempo real sem expor dados publicamente.
2. **Higienização e Validação Automática de Dados:**
   * **CPF:** Aplica a verificação do cálculo de Módulo 11 (algoritmo oficial da Receita Federal). Valida se o número existe e aplica a máscara `000.000.000-00`.
   * **Telefone/WhatsApp:** Detecta variações de contato, remove DDI (`+55`), ajusta a quantidade de dígitos e padroniza para `(XX) XXXXX-XXXX`.
3. **Triagem Visual Dinâmica (OpenPyXL):**
   Células com inconsistências são destacadas automaticamente no arquivo Excel gerado:
   * 🔴 **Vermelho:** CPFs matematicamente inválidos.
   * 🟠 **Laranja:** Telefones fora do padrão de digitação.
4. **Interface Leve e Não-Bloqueante:** 
   Desenvolvida com `Tkinter` e suporte a `Threading`, garantindo que a interface gráfica permaneça fluida e sem congelar enquanto busca as requisições na API.

---

## ⚙️ Como Configurar a Conexão com a Google Sheets API

Para rodar a automação integrada à nuvem:

1. Acesse o **Google Cloud Console** e crie um novo projeto.
2. Ative as APIs **Google Sheets API** e **Google Drive API**.
3. Em **IAM e Administrador > Contas de Serviço**, crie uma Conta de Serviço e gere uma chave de acesso em formato `.json`.
4. Compartilhe a planilha do Google Sheets com o e-mail gerado para a Conta de Serviço (concedendo acesso de Editor ou Leitor).
5. Defina no arquivo `main.py` o nome do arquivo da chave `.json` e o `ID_PLANILHA_GOOGLE`.

---

## 🛠️ Tecnologias Utilizadas

- **Python 3.13**
- **gspread & oauth2client:** Autenticação OAuth2 e comunicação com as APIs do Google Cloud.
- **Pandas:** Leitura, tratamento e manipulação estruturada de dados.
- **OpenPyXL:** Leitura, gravação e aplicação de estilos/cores nas células do Excel.
- **Tkinter & Threading:** Interface gráfica e gerenciamento de tarefas assíncronas.
- **PyInstaller:** Compilação da aplicação em executável autônomo `.exe` para o usuário final.

## 📚 Referências e Créditos

Este projeto teve como base de estudo e inspiração para a integração com a API a aula de automação em Python da **Asimov Academy**. 
- Assista ao vídeo de referência:  [ Integração Google Sheets com Python - Do Básico ao Avançado](https://www.youtube.com/watch?v=6XaF4ZF7LW0).