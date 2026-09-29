# Stocky — Arquitetura Inicial

## Stack

- Web: Next.js + React + TypeScript
- Mobile: React Native + Expo + TypeScript
- API: NestJS + TypeScript
- Banco: PostgreSQL
- ORM: Prisma
- Estado/Server state: TanStack Query
- Estado local pontual: Zustand
- Validação: Zod onde fizer sentido
- Containers locais: Docker
- Versionamento: GitHub

## Monorepo

```
apps/
  web/
  mobile/
  api/

packages/
  ui/
  types/
  database/
  config/

docs/
```

## Regras de arquitetura

1. O banco é a fonte de verdade.
2. Regras críticas de estoque e movimentação ficam no backend.
3. Web e mobile não devem duplicar regras de domínio.
4. O mobile deve tolerar conectividade intermitente desde que a segurança/consistência da operação seja preservada.
5. QR Code identifica localização; o backend decide se a operação pode ser confirmada.
6. Nenhuma funcionalidade de mapa deve ser necessária para o núcleo funcionar.
7. Evitar dependências e infraestrutura que ainda não tenham necessidade real.

## Primeira entrega técnica

Criar a fundação:
- workspaces/monorepo
- lint
- format
- testes
- Docker para desenvolvimento
- API inicial
- Web inicial
- Mobile inicial
- Prisma inicial
- variáveis de ambiente de exemplo
- documentação de desenvolvimento

Ainda não implementar todas as telas de negócio.
