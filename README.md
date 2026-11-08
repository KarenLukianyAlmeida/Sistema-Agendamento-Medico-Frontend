# Sistema de Agendamento Médico — Front-end

Repositório do Front-end da aplicação web desenvolvida para a gestão e agendamento de consultas médicas. O projeto integra uma Landing Page responsiva e uma aplicação interativa em React conectada a uma API RESTful em Node.js.

---

## 🚀 Tecnologias Utilizadas

* **React (Vite)** — Biblioteca JavaScript para construção da interface de usuário.
* **TypeScript** — Tipagem estática para maior segurança e escalabilidade.
* **Axios** — Cliente HTTP para consumo dos endpoints da API REST.
* **React Router Dom** — Gestão de rotas e proteção de páginas privadas.
* **HTML5 Semântico & CSS3** — Estrutura e estilização responsiva (Mobile-First, Flexbox e CSS Grid).

---

## 🛠️ Funcionalidades Implementadas (17 Endpoints Integrados)

O sistema conta com autenticação baseada em papéis (**RBAC** — *Role-Based Access Control*), diferenciando Pacientes, Médicos e Administradores:

### Autenticação e Perfis (`/auth`, `/users`)
1. **Criar Conta** (`POST /api/auth/register`) — Registo de novos utilizadores (Público).
2. **Fazer Login** (`POST /api/auth/login`) — Autenticação e emissão do token JWT (Público).
3. **Ver Perfil Logado** (`GET /api/users/me`) — Consulta dos dados do utilizador autenticado.
4. **Atualizar Meu Perfil** (`PUT /api/users/me`) — Edição de dados cadastrais.
5. **Listar Todos os Usuários** (`GET /api/users`) — Listagem geral restrita a administradores (`ADMIN`).

### Catálogo de Médicos e Especialidades (`/doctors`, `/specialties`)
6. **Listar Especialidades** (`GET /api/specialties`) — Catálogo de especialidades médicas disponíveis.
7. **Listar Médicos** (`GET /api/doctors`) — Listagem do corpo clínico com suporte a filtros.
8. **Detalhes do Médico** (`GET /api/doctors/:id`) — Visualização de perfil e currículo do profissional.
9. **Cadastrar Médico** (`POST /api/doctors`) — Registo de novo médico (`ADMIN`).
10. **Atualizar Médico** (`PUT /api/doctors/:id`) — Alteração de dados do médico (`ADMIN` ou próprio).

### Disponibilidade e Horários (`/availability`)
11. **Ver Agenda Livre** (`GET /api/doctors/:doctorId/availability`) — Consulta de horários livres por data.
12. **Cadastrar Horários** (`POST /api/doctors/:doctorId/availability`) — Gestão da escala de atendimento.
13. **Remover Horário** (`DELETE /api/doctors/:doctorId/availability/:id`) — Bloqueio ou remoção de horário da grade.

### Gestão de Consultas (`/appointments`)
14. **Listar Consultas** (`GET /api/appointments`) — Visualização de agendamentos filtrados por perfil (Paciente, Médico ou Admin).
15. **Detalhes da Consulta** (`GET /api/appointments/:id`) — Consulta de pormenores de um agendamento específico.
16. **Agendar Consulta** (`POST /api/appointments`) — Marcação de nova consulta (`PATIENT` ou `ADMIN`).
17. **Cancelar Consulta** (`DELETE /api/appointments/:id`) — Cancelamento de agendamento prévio.

---

## 📂 Estrutura do Projeto

```text
src/
├── assets/          # Imagens, vídeos e ficheiros multimédia (.vtt)
├── components/      # Componentes reutilizáveis (Botões, Cards, Inputs, Modais)
├── pages/           # Ecrãs principais (Home, Login, Dashboard, Médico, Consultas)
├── routes/          # Configuração de rotas públicas e privadas (React Router)
├── services/        # Configuração do Axios e serviços de integração com a API
├── types/           # Definições de interfaces e tipos TypeScript
├── App.tsx          # Componente raiz
└── main.tsx         # Ponto de entrada da aplicação Vite
