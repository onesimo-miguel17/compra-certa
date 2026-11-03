# Compra Certa

**Plataforma SaaS de comércio electrónico multi-loja.**

O Compra Certa permite que comerciantes criem e administrem lojas online independentes, com catálogo, inventário, encomendas, pagamentos e expedição num único produto.

> Estado: fundação técnica em preparação. Ainda não está pronto para produção e não processa pagamentos reais.

## Princípios do produto

- **Multi-tenant:** cada loja tem os seus próprios dados e utilizadores autorizados.
- **Isolamento por defeito:** nenhuma loja pode consultar ou alterar dados de outra.
- **Comerciante titular dos pagamentos:** cada comerciante liga a sua própria conta de pagamento, após validação do fornecedor.
- **Operação logística híbrida:** processos manuais continuam disponíveis mesmo quando uma integração externa falha.
- **Angola primeiro:** AOA (Kz) e português como configuração inicial, com base preparada para internacionalização.
- **Segurança e auditabilidade:** permissões, políticas na base de dados, registos de auditoria e webhooks idempotentes.

## Arquitectura prevista

- Next.js App Router, React e TypeScript
- Tailwind CSS
- Supabase: PostgreSQL, Auth e Storage
- Vercel para alojamento da aplicação
- AppyPay como candidato inicial a gateway, sujeito à validação documental, contratual e técnica
- Adaptadores para fornecedores de pagamentos e logística
- Subdomínios para lojas, com domínio próprio numa fase posterior

A resolução do domínio identifica a loja, mas **não substitui autorização**. O isolamento é aplicado no servidor e na base de dados, com políticas RLS.

## Estrutura

~~~text
src/
  app/                 # rotas e layouts Next.js
  components/          # componentes partilhados
  modules/             # módulos de negócio por domínio
  infrastructure/      # integrações externas
  lib/                 # utilitários e configuração
  config/
  types/
supabase/
  migrations/
  seed.sql
docs/
  architecture/
  database/
  integrations/
  operations/
  security/
tests/
  unit/
  integration/
  security/
  e2e/
~~~

## Requisitos

- Node.js LTS compatível com a versão de Next.js instalada
- npm
- Projecto Supabase (não criado automaticamente)
- Variáveis de ambiente configuradas a partir de .env.example

## Desenvolvimento local

1. Clonar o repositório:
   ~~~bash
   git clone https://github.com/onesimo-miguel17/compra-certa.git
   cd compra-certa
   ~~~
2. Instalar dependências:
   ~~~bash
   npm install
   ~~~
3. Copiar .env.example para .env.local e preencher as variáveis quando o projecto Supabase estiver configurado.
4. Iniciar:
   ~~~bash
   npm run dev
   ~~~

Verificações:
~~~bash
npm run lint
npm run typecheck
npm run build
~~~

## Segurança

- Nunca expor chaves secretas ou credenciais de comerciantes no browser.
- Aplicar RLS em todas as tabelas com dados de tenant.
- Validar sempre a associação entre utilizador, loja e recurso no servidor.
- Validar assinatura/autenticidade dos webhooks e processá-los de forma idempotente.
- Não confiar em store_id, preços ou totais enviados pelo cliente.
- Não guardar dados de cartão; usar os fluxos suportados pelo fornecedor de pagamento.

## Integrações e limitações conhecidas

A integração AppyPay **não está implementada nem confirmada**. Antes do desenvolvimento do adaptador, validar documentação oficial actual, contrato comercial, credenciais de sandbox/produção, suporte a múltiplos comerciantes, autenticação de webhooks, pagamentos, reembolsos e liquidação.

O mesmo princípio aplica-se aos transportadores: nenhum fornecedor foi seleccionado. O fluxo manual será mantido como alternativa operacional.

## Documentação

- [Visão de arquitectura](docs/architecture/overview.md)
- [Backlog inicial](docs/roadmap/backlog.md)

## Estado do projecto

Este repositório é independente do website institucional Onésimo Digital. A demonstração anteriormente existente no Onésimo Digital permanece separada e não é a aplicação de produção do Compra Certa.
