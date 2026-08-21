# Atividade de Fixação — TADS Bibliotecário

> Contexto: sistema bibliotecário para as escolas do **IFES**, analisado sob a ótica de **desenvolvedor + QA**, com atenção a usabilidade, disponibilidade, escalabilidade, segurança, acessibilidade e responsividade.

---

## 1. Qual problema a biblioteca pretende resolver

Controlar o **empréstimo de livros** das escolas do IFES de forma segura e automatizada — permitindo consultar o catálogo, solicitar empréstimos e devolver no prazo, respeitando o **limite de livros por usuário**, o **prazo de devolução** e a **disponibilidade de cada exemplar**. Substitui o controle manual, reduzindo erros como emprestar um exemplar indisponível ou perder o controle de atrasos.

## 2. Três stakeholders e o que cada um espera

| Stakeholder | O que espera do sistema |
|---|---|
| **Estudante / Professor** | Consultar o acervo e pegar/devolver livros de forma simples, rápida e acessível (usabilidade e responsividade). |
| **Bibliotecário** | Administrar o acervo e acompanhar empréstimos/atrasos com confiabilidade e sem retrabalho (disponibilidade). |
| **Gestor do IFES** | Cumprir políticas e a LGPD, com dados seguros e um serviço que escala para várias escolas (segurança e escalabilidade). |

## 3. Dois elementos do sistema e dois externos

- **Pertencem ao sistema:**
  1. Consulta ao catálogo / gestão do acervo.
  2. Registro e validação de empréstimos e devoluções.
- **Permanecem externos:**
  1. Definição das políticas de empréstimo (decisão de gestores).
  2. Catalogação/descarte físico dos livros e cobrança de multa no balcão.

## 4. Por que cada atividade pertence à sua etapa

- **Definir regras → Análise:** o foco é *entender o problema e o negócio* — quem pode emprestar, quantos livros, qual prazo, o que ocorre em atraso. São decisões de **o quê** o sistema deve respeitar, antes de qualquer código.
- **Organizar a solução → Projeto:** decide-se *como* atender essas regras — classes (`Usuário`, `Livro`, `Empréstimo`) e a divisão de responsabilidades entre interface, serviço e banco de dados. É a **arquitetura** que dá forma à solução.
- **Criar o software → Implementação:** as decisões viram **telas, código e tabelas** executáveis. Cada linha de código responde a uma regra da análise, através da estrutura definida no projeto — garantindo rastreabilidade.

## 5. Perguntas de viabilidade

- **Técnica:** O IFES possui infraestrutura de hospedagem, integração com o cadastro de alunos e equipe capaz de manter o sistema disponível e escalável para todas as escolas?
- **Operacional:** Os bibliotecários e estudantes conseguem adotar o novo processo digital sem reduzir a eficiência do atendimento e sem barreiras de acessibilidade?
