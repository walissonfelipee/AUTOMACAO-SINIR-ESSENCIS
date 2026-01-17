# Automação SINIR MTR – Processamento de MTRs em Python

## Descrição

Projeto de automação desenvolvido em Python para operar no sistema SINIR MTR, utilizado por empresas de descarte de resíduos.

A automação tem como objetivo realizar o processamento e a baixa de MTRs de forma automática a partir de uma planilha de dados, eliminando a necessidade de preenchimento manual repetitivo e reduzindo erros operacionais.

Após a configuração inicial, todo o processo ocorre de forma autônoma, com monitoramento de progresso e tratamento de falhas.

---

## Pré-requisitos

- Google Chrome instalado  
- Acesso à internet  
- Planilha de dados no mesmo diretório do projeto  
- Credenciais de acesso ao sistema SINIR (configuradas previamente pelo desenvolvedor)

---

## Funcionamento Geral

1. O usuário posiciona a planilha com os dados na mesma pasta do bot  
2. A automação é iniciada (única interação necessária do usuário)  
3. O bot:
   - Abre o navegador automaticamente
   - Acessa o site do SINIR
   - Realiza o login com credenciais previamente configuradas
   - Navega até a página específica de lançamento e baixa de MTRs
4. Para cada linha da planilha, a automação:
   - Insere os dados no sistema SINIR, como:
     - Nome do motorista
     - Placa do caminhão
     - Tecnologia do resíduo
     - Peso
     - Data de entrada
   - Realiza rateio de peso quando necessário
   - Finaliza a baixa da MTR
5. O processo segue até o final da planilha ou até interrupção manual

---

## Execução Visual no Navegador

A automação é executada com o navegador aberto, permitindo a visualização em tempo real
das interações realizadas no sistema SINIR.

Durante a execução, é possível acompanhar o bot navegando pelas páginas,
preenchendo formulários, realizando validações e finalizando a baixa das MTRs,
simulando o comportamento de um usuário humano.

---

## Interface de Acompanhamento (Tkinter)

O projeto conta com uma interface simples desenvolvida em Tkinter, utilizada exclusivamente
para acompanhamento da execução da automação.

A interface exibe:
- Linha atual da planilha em processamento  
- Progresso geral da execução  
- Status da automação (em execução, pausada, finalizada)  

Essa interface evita incertezas sobre o tempo restante da execução, especialmente em cenários
com grande volume de registros.

---

## Tratamento de Erros e Resiliência

A automação foi projetada para lidar com falhas comuns em processos longos, incluindo:

- Validação de dados da planilha  
  - Exemplo: MTRs que deveriam conter 12 dígitos, mas estão cadastradas com quantidade incorreta  
- Erros de preenchimento exigidos pelo SINIR  
- Queda de conexão com a internet  
  - O bot aguarda a reconexão e retoma a execução automaticamente do ponto onde parou  
- Interrupção manual da automação  
  - O progresso é salvo para permitir retomada posterior  
- Erros que impedem a execução de uma linha específica  
  - A linha é registrada em uma planilha separada com a descrição do problema  
  - A automação continua para a próxima linha  

---

## Relatório Final

Ao final da execução, o sistema envia automaticamente um e-mail contendo:
- A planilha com os registros que não puderam ser processados  
- Informações para análise e resolução manual dos casos pendentes  

---

## Tecnologias e Bibliotecas Utilizadas

- Python  
- Selenium WebDriver  
- Tkinter  
- Pandas  
- OpenPyXL  
- WebDriver Manager  
- Threading  
- Logging  
- PyAutoGUI  
- Dotenv  
- SMTP (envio de e-mails)  
- Manipulação de arquivos e sistema operacional  

---

## Observações

Este projeto não possui interface gráfica de usuário final.  
A execução da automação ocorre de forma visual através do navegador, permitindo
o acompanhamento das ações realizadas no sistema web.

A interface em Tkinter tem finalidade exclusivamente informativa, sendo utilizada
apenas para monitoramento do progresso da execução.

---