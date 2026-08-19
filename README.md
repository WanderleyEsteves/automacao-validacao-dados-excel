# 📊 Sistema de Sincronização, Validação e Automação de Dados em Excel

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![OpenPyXL](https://img.shields.io/badge/OpenPyXL-GREEN?style=for-the-badge)
![Tkinter](https://img.shields.io/badge/Tkinter-GUI-blue?style=for-the-badge)

Aplicação desktop em Python desenvolvida para automatizar a busca de respostas em formulários na nuvem, validar dados cadastrais e atualizar planilhas Excel localmente sem trabalho manual.

---

## 🎯 O Problema

Trabalhar com cadastro de pessoas costuma virar um gargalo operacional rapidamente quando a coleta é feita de forma descentralizada (por mensagens de WhatsApp, e-mails ou formulários sem integração):
- **Gasto de tempo absurdo:** A equipe precisa abrir mensagem por mensagem, copiar dados e colar linha por linha na planilha interna.
- **Trabalho repetitivo:** Dezenas de horas jogadas fora com digitação manual que poderiam ser usadas para tarefas mais importantes.
- **Dados incorretos no sistema:** Pessoas digitam CPFs errados ou esquecem o DDD no telefone. Sem uma checagem rápida, esses erros vão parar direto na base da empresa.

---

## 🚀 Como a Ferramenta Resolve Isso

O sistema faz a ponte entre a resposta do formulário e a planilha final da empresa em poucos segundos:

1. **Sincronização com 1 Clique:** O operador clica no botão da ferramenta e o script busca as respostas mais recentes direto da nuvem, alimentando o Excel automaticamente. Chega de copiar e colar.
2. **Tratamento e Validação Automática:**
   * **CPF:** Executa o cálculo real do módulo 11 (algoritmo da Receita Federal) para checar se o CPF existe e aplica a formatação `000.000.000-00`.
   * **Telefone:** Remove o `+55`, ajusta a quantidade de dígitos e padroniza para o formato `(XX) XXXXX-XXXX`.
3. **Alertas Visuais para Triagem:** Usando o `OpenPyXL`, o script pinta as células diretamente no Excel quando encontra um dado suspeito — **vermelho** para CPFs inválidos e **laranja** para telefones fora do padrão. Assim, a equipe sabe exatamente o que precisa conferir antes de dar andamento.
4. **Prático e Leve:** Uma janela simples criada com `Tkinter` (usando `Threading` para a tela não travar enquanto baixa os dados), compilada em um arquivo `.exe` pronto para rodar em qualquer Windows.

---

### ⚙️ Como Configurar as Credenciais

1. Crie um projeto no **Google Cloud Console**.
2. Ative as APIs **Google Sheets API** e **Google Drive API**.
3. Crie uma **Conta de Serviço (Service Account)** e baixe o arquivo de chave `.json`.
4. Compartilhe a planilha do Google com o e-mail da Conta de Serviço.
5. Preencha as variáveis `NOME_ARQUIVO_JSON` e `ID_PLANILHA_GOOGLE` no arquivo `main.py`.

---

>>>>>>> b093287 (docs: atualizacao do README)
## 🛠️ Tecnologias Utilizadas

---

- **Python 3.13**
- **Pandas:** Manipulação, limpeza e estruturação dos dados.
- **OpenPyXL:** Leitura, gravação e formatação de estilos/cores nas células do Excel.
- **Tkinter & Threading:** Interface visual leve e execução em segundo plano.
- **PyInstaller:** Transforma o script em executável autônomo para o usuário final.

