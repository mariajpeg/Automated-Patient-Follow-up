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

**Resultados**

Foram realizados testes com diferentes datas de atendimento, incluindo casos em dias úteis e na sexta-feira, para verificar o cálculo correto da data de acompanhamento e o funcionamento do fluxo de notificações.

**Status:** MVP funcional em desenvolvimento.

## Limitações e melhorias futuras

Esta primeira versão foi desenvolvida com foco na automação do registro e no envio de lembretes de acompanhamento. Algumas funcionalidades podem ser aprimoradas em versões futuras:

- **Feriados:** implementar um calendário de feriados nacionais para tornar o cálculo de dias úteis mais preciso.
- **Atualização de status:** automatizar a atualização do status do acompanhamento após o envio do lembrete.
- **Tratamento de erros:** aprimorar a identificação e o registro de falhas durante a execução do workflow.
- **Interface:** melhorar a experiência visual do formulário de cadastro.

Essas melhorias fazem parte da evolução planejada do projeto.

## Segurança e privacidade

O projeto foi desenvolvido considerando a importância da proteção de dados pessoais, especialmente por envolver um cenário relacionado à área da saúde.

Algumas medidas e cuidados adotados:

- **Dados fictícios:** as demonstrações do projeto utilizam informações fictícias, sem exposição de dados reais de pacientes.
- **Envio manual de mensagens:** a automação gera um lembrete por e-mail com uma sugestão de mensagem, mas o contato com o paciente é realizado manualmente, após revisão.
- **Credenciais:** informações de autenticação e dados privados de integração não devem ser compartilhados no repositório público.
- **Privacidade:** o projeto não realiza diagnósticos, interpreta sintomas ou recomenda tratamentos.

Por se tratar de um protótipo, sua utilização em um ambiente clínico real exigiria uma avaliação adicional de segurança, controle de acesso e conformidade com a Lei Geral de Proteção de Dados (LGPD).
