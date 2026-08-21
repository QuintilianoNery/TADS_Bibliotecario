# Biblioteca Digital — Documentação Inicial de Requisitos

> Documento inicial de levantamento de requisitos do sistema de **Biblioteca Digital** de uma escola.
> O objetivo é identificar cedo as **fronteiras do sistema** — o que será tratado de forma automatizada e o que continuará sendo manual — reduzindo retrabalho e riscos ao longo do projeto.

---

## 1. Contexto e Visão Geral

Uma escola quer um sistema para **controlar o empréstimo de livros**. Os usuários devem poder consultar o catálogo, solicitar empréstimos e devolver os livros dentro do prazo. Os bibliotecários administram o acervo e definem as regras de empréstimo.

**Necessidade principal:** permitir empréstimos com segurança, respeitando o **limite de livros**, o **prazo de devolução** e a **disponibilidade de cada exemplar**.

Quanto mais cedo identificarmos as fronteiras do sistema, melhor conseguimos separar aquilo que o sistema fará automaticamente daquilo que continuará dependendo de decisão ou ação humana.

---

## 2. Fronteiras do Sistema (Escopo)

### 2.1. O que será tratado pelo sistema (automatizado)

- Consulta ao catálogo de livros (busca por título, autor, categoria, disponibilidade).
- Solicitação de empréstimo pelo usuário.
- Controle de disponibilidade de cada exemplar (quantos existem, quantos estão emprestados).
- Registro de empréstimos e devoluções.
- Cálculo do prazo de devolução e verificação de atraso.
- Aplicação automática das regras de empréstimo (limite de livros por usuário, disponibilidade, prazo).
- Notificações de vencimento e de livros disponíveis (reservas).
- Gestão interna do acervo (cadastro, edição e baixa de livros/exemplares).

### 2.2. O que continuará sendo manual (fora do escopo do sistema)

- **Definição das políticas de empréstimo** (quantidade de dias, limite de livros, valor de multa): decidido por gestores/bibliotecários — o sistema apenas **aplica** a regra configurada.
- Compra, catalogação física e descarte de livros físicos.
- Cobrança/pagamento de multas em dinheiro no balcão (o sistema apenas registra a pendência).
- Atendimento presencial e mediação de conflitos.

> **Fronteira-chave:** *Consultar o catálogo* é **gestão interna** (dentro do sistema). *Definir políticas de empréstimo* é **externo** (decisão humana que alimenta as configurações do sistema).

---

## 3. Perguntas Norteadoras

### 3.1. Quem utilizará o sistema? O bibliotecário? Os estudantes? Ambos?

**Ambos**, com perfis e permissões diferentes:

- **Estudantes (e professores):** consultam o catálogo, solicitam empréstimos, acompanham prazos e devolvem livros.
- **Bibliotecários:** administram o acervo, configuram as regras de empréstimo (dentro das políticas definidas pela gestão) e acompanham os empréstimos.

### 3.2. Quais regras precisam ser respeitadas?

- **Limite de livros** emprestados simultaneamente por usuário.
- **Prazo de devolução** definido para cada empréstimo.
- **Disponibilidade do exemplar**: só é possível emprestar um exemplar disponível.
- Usuário com **pendências** (atraso/multa) pode ter novos empréstimos bloqueados.
- Regras de acesso por perfil (estudante ≠ bibliotecário).
- Respeito a **direitos autorais** e às regras de acesso do acervo.

### 3.3. Quais dados serão tratados?

- **Usuários:** nome, matrícula/identificação, perfil (estudante, professor, bibliotecário), contato.
- **Acervo:** livros (título, autor, ISBN, categoria) e exemplares (código, estado, disponibilidade).
- **Empréstimos:** usuário, exemplar, data de retirada, data prevista de devolução, data de devolução real, status.
- **Reservas** e **notificações**.
- **Políticas/configurações:** limites, prazos e regras vigentes.

> Como há **dados pessoais**, o tratamento deve respeitar a **LGPD** (finalidade, minimização e segurança dos dados).

### 3.4. Quais riscos podem impedir o projeto?

- **Técnico:** falta de infraestrutura, integração ou equipe para manter o serviço.
- **Econômico:** custo de licenças, hospedagem e suporte acima do orçamento.
- **Operacional:** resistência à mudança; bibliotecários/usuários não adotarem o novo processo.
- **Jurídico:** descumprimento de direitos autorais ou da proteção de dados (LGPD).
- **Temporal:** atraso na implantação em relação ao calendário escolar e às dependências do projeto.
- **Qualidade dos dados:** acervo cadastrado de forma incompleta ou inconsistente.

---

## 4. Stakeholders e Responsabilidades

| Stakeholder | Papel / Responsabilidade |
|---|---|
| **Estudantes e professores** | Utilizam o serviço: consultam o catálogo, solicitam e devolvem livros dentro do prazo. |
| **Bibliotecários** | Administram o acervo (cadastro/baixa de livros e exemplares) e operam o sistema no dia a dia. |
| **Gestores** | Definem as **políticas** (limites, prazos, regras de acesso e multas). Responsabilidade **externa** ao sistema. |
| **Desenvolvedores** | Mantêm, evoluem e dão suporte ao sistema; garantem segurança, disponibilidade e correção. |

---

## 5. Análise de Viabilidade

| Dimensão | Pergunta-chave |
|---|---|
| **Técnica** | A biblioteca possui infraestrutura, integração e equipe capaz de manter o serviço? |
| **Econômica** | A instituição pode pagar pelas licenças, hospedagem e suporte necessários? |
| **Operacional** | Bibliotecários e usuários conseguem adotar o novo processo sem reduzir a eficiência? |
| **Jurídica** | O serviço respeita direitos autorais, regras de acesso e proteção de dados (LGPD)? |
| **Temporal** | A implantação está alinhada ao calendário, considerando as dependências do projeto? |

---

## 6. Requisitos Funcionais (RF)

| ID | Requisito | Ator |
|---|---|---|
| **RF01** | Consultar o catálogo por título, autor, categoria e disponibilidade. | Estudante / Bibliotecário |
| **RF02** | Autenticar usuários e diferenciar perfis (estudante, professor, bibliotecário). | Todos |
| **RF03** | Solicitar empréstimo de um exemplar disponível. | Estudante / Professor |
| **RF04** | Validar automaticamente as regras no empréstimo (limite de livros, disponibilidade, prazo e pendências). | Sistema |
| **RF05** | Registrar a devolução do exemplar e atualizar sua disponibilidade. | Estudante / Bibliotecário |
| **RF06** | Calcular a data prevista de devolução e identificar atrasos. | Sistema |
| **RF07** | Reservar um livro indisponível e notificar quando ficar disponível. | Estudante / Professor |
| **RF08** | Gerenciar o acervo: cadastrar, editar e dar baixa em livros e exemplares. | Bibliotecário |
| **RF09** | Configurar as regras de empréstimo (limite, prazo) conforme a política vigente. | Bibliotecário |
| **RF10** | Consultar o histórico de empréstimos e as pendências do usuário. | Estudante / Bibliotecário |
| **RF11** | Emitir notificações de vencimento e de atraso. | Sistema |

---

## 7. Requisitos Não Funcionais (RNF)

| ID | Categoria | Requisito |
|---|---|---|
| **RNF01** | Segurança | Controle de acesso por perfil; senhas armazenadas de forma criptografada. |
| **RNF02** | Privacidade / Legal | Tratamento de dados pessoais em conformidade com a **LGPD**. |
| **RNF03** | Usabilidade | Interface simples e intuitiva, adequada a estudantes e bibliotecários. |
| **RNF04** | Desempenho | A consulta ao catálogo deve responder em até ~2 segundos em condições normais. |
| **RNF05** | Disponibilidade | Sistema disponível durante o horário de funcionamento da biblioteca. |
| **RNF06** | Integridade | Garantir consistência: um mesmo exemplar não pode ser emprestado a dois usuários simultaneamente. |
| **RNF07** | Compatibilidade | Acesso via navegador em desktop e dispositivos móveis (responsivo). |
| **RNF08** | Manutenibilidade | Código organizado e documentado, permitindo evolução pela equipe de desenvolvimento. |
| **RNF09** | Auditabilidade | Registro (log) das operações de empréstimo e devolução para rastreabilidade. |

---

## 8. Da Análise à Implementação

Cada decisão técnica deve responder a uma **necessidade** ou **regra** identificada. O caminho percorre três etapas:

1. **Análise** — Identificamos os usuários e esclarecemos as regras: quem pode emprestar, quantos livros cada pessoa pode retirar, qual é o prazo e o que acontece em caso de atraso.
2. **Projeto** — Definimos classes como **Usuário**, **Livro** e **Empréstimo** e distribuímos responsabilidades entre **interface**, **serviço** e **banco de dados**.
3. **Implementação** — Transformamos essas decisões em **telas**, **código** e **tabelas**.

Assim, cada elemento técnico é rastreável até a regra de negócio que o originou:

| Regra identificada (Análise) | Decisão de projeto | Implementação |
|---|---|---|
| Quem pode emprestar (perfil) | Classe `Usuário` com perfil e autenticação | Tela de login + tabela `usuario` |
| Limite de livros por pessoa | Regra na camada de **serviço** de empréstimo | Validação no código + consulta ao banco |
| Prazo de devolução | Atributo de prazo na classe `Empréstimo` | Cálculo de data + tabela `emprestimo` |
| O que acontece em atraso | Regra de status/pendência no serviço | Notificação + registro de pendência |
| Disponibilidade do exemplar | Relação `Livro` ↔ `Exemplar` | Controle de estoque na tabela `exemplar` |

---

## 9. Próximos Passos

1. Validar este documento com bibliotecários e gestores.
2. Detalhar os casos de uso principais (empréstimo, devolução, reserva).
3. Modelar os dados (usuários, acervo, empréstimos).
4. Priorizar os requisitos para a primeira versão (MVP).
