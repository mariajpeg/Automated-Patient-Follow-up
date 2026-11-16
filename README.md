# Automated-Patient-Follow-up
### Automação inteligente de acompanhamento pós-atendimento

**Sobre o projeto**

É um projeto de automação desenvolvido para organizar o acompanhamento administrativo de pacientes após atendimentos odontológicos.

A proposta surgiu da identificação de um problema operacional: a dificuldade de manter uma rotina consistente de acompanhamento, principalmente quando os atendimentos acontecem às sextas-feiras e o contato precisa ser realizado no próximo dia útil.

**Objetivo**

Automatizar o registro dos atendimentos, calcular a data prevista para acompanhamento e gerar lembretes por e-mail com mensagens previamente preparadas para revisão humana.

**Tecnologias utilizadas**
- n8n — orquestração do workflow.
- Python — validação dos dados e cálculo de dias úteis.
- Google Sheets — armazenamento e controle dos registros.
- Gmail — envio de lembretes administrativos.

**Funcionamento**

1. O usuário preenche um formulário.
2. O Python valida os dados e calcula o próximo dia útil.
3. Os registros são organizados na planilha de controle.
4. O workflow aguarda a data programada.
5. Um e-mail é enviado ao responsável com o lembrete e uma mensagem sugerida para revisão.

**Regra de negócio**

O acompanhamento é programado para um dia útil após o atendimento. Sábados e domingos são desconsiderados.

**Segurança e limitações**

O projeto utiliza dados fictícios para demonstração. Não realiza diagnóstico, recomendações clínicas ou envio automático de mensagens aos pacientes. O contato permanece sob revisão e responsabilidade humana.

**Resultados**

Foram realizados testes com diferentes datas de atendimento, incluindo casos em dias úteis e na sexta-feira, para verificar o cálculo correto da data de acompanhamento e o funcionamento do fluxo de notificações.

**Status:** MVP funcional em desenvolvimento.
