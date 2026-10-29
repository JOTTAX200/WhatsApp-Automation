# 🤖 Automação de Mensagens no WhatsApp com n8n

Automação de envio de mensagens para grupos do WhatsApp utilizando **n8n, Docker e WAHA**, com agendamento semanal, verificação de dias da semana e consulta de feriados nacionais, estaduais e municipais.

## 📌 Sobre o projeto

Este projeto foi desenvolvido para automatizar o envio de uma mensagem recorrente no WhatsApp, evitando a necessidade de enviá-la manualmente todos os dias programados.

A automação utiliza um fluxo visual no n8n para organizar as etapas de agendamento, consulta de feriados, validação das condições e envio da mensagem por meio da API do WAHA.

## 🖼️ Telas do projeto

### Fluxo da automação
![image alt]((https://github.com/JOTTAX200/WhatsApp-Automation/blob/main/Fluxo%20da%20Automacao.png?raw=true))

### Resultado
![image alt](https://github.com/JOTTAX200/BiblioWeb/blob/main/Livros%20Principais.png?raw=true)

## ⚙️ Funcionalidades

- ⏰ **Agendamento automático:** execução programada para terça-feira, quarta-feira e quinta-feira, às 12h.
- 📅 **Verificação do dia da semana:** valida se o dia atual corresponde a um dos dias permitidos.
- 🇧🇷 **Consulta de feriados:** integração com a BrasilAPI para consultar feriados nacionais e estaduais de São Paulo.
- 🏙️ **Feriados municipais:** verificação de feriados específicos de Jundiaí, São Paulo.
- 🚫 **Envio condicional:** impede o envio da mensagem quando um feriado reconhecido é identificado.
- 💬 **Integração com WhatsApp:** envio automatizado de mensagens para um grupo específico.

## 🧰 Tecnologias utilizadas

| Tecnologia | Finalidade |
|---|---|
| [n8n](https://n8n.io/) | Criação e execução do fluxo de automação |
| [Docker](https://www.docker.com/) | Execução dos serviços em containers |
| [WAHA](https://waha.devlike.pro/) | Integração com o WhatsApp por API |
| [BrasilAPI](https://brasilapi.com.br/docs) | Consulta de feriados nacionais e estaduais |
| JavaScript | Validação das datas e regras do fluxo |

## 🔄 Como funciona o fluxo

1. **Schedule Trigger:** inicia a automação nos dias e horários configurados.
2. **Validação do dia da semana:** permite continuar somente nos dias definidos.
3. **Consultar Feriados:** realiza uma requisição HTTP à BrasilAPI.
4. **Verificar Feriado:** analisa os dados recebidos e verifica os feriados municipais configurados no código.
5. **If:** decide se a execução pode continuar.
6. **HTTP Request:** envia a mensagem ao grupo do WhatsApp por meio do WAHA, somente quando as condições forem atendidas.

## 📨 Exemplo de mensagem

> Boa tarde tia, hoje eu vou

A mensagem pode ser personalizada diretamente na configuração do node HTTP Request responsável pelo envio.

## 🚀 Configuração e execução

### Pré-requisitos

- Docker instalado e funcionando.
- n8n configurado.
- WAHA em execução e com a sessão do WhatsApp conectada.
- Acesso ao grupo de destino e seu identificador (`chatId`).
- Workflow configurado com os nodes e as conexões necessárias.

### Passos para executar

1. Inicie os containers do n8n e do WAHA.
2. Acesse a interface do n8n.
3. Configure o Schedule Trigger com os dias e o horário desejados.
4. Configure a consulta de feriados utilizando a BrasilAPI.
5. Ajuste as condições e o código JavaScript de validação.
6. Configure o HTTP Request para enviar a mensagem pelo WAHA.
7. Teste os nodes individualmente, evitando disparar mensagens reais durante os testes.
8. Ative o workflow para iniciar a execução automática.

## 🔐 Segurança

- Não publique chaves de API, senhas, tokens ou credenciais no repositório.
- Não exponha a interface do WAHA diretamente à internet sem as devidas proteções.
- Utilize variáveis de ambiente para configurações sensíveis.
- Remova identificadores reais de grupos e números de telefone de exemplos públicos.

## ⚠️ Observações

- O computador ou servidor que executa os containers precisa permanecer ligado para que a automação funcione no horário programado.
- A configuração de feriados municipais deve ser revisada conforme o calendário oficial de cada ano.
- Pontos facultativos, como Carnaval, precisam ser adicionados separadamente caso também devam impedir o envio.
- Caso a consulta de feriados falhe, o fluxo deve ser configurado para interromper a execução, evitando enviar a mensagem sem validar o calendário.
- O comportamento do WAHA depende da sessão conectada e da configuração da instalação utilizada.

## 🎯 Objetivo do projeto

Aplicar conceitos de automação de processos, integração entre APIs, lógica condicional e execução de serviços em containers, utilizando ferramentas que podem ser aplicadas em projetos pessoais e profissionais.

---

Desenvolvido como projeto prático de automação utilizando n8n, Docker, WAHA e JavaScript.
