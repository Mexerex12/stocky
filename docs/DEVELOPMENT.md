# Stocky — Guia de Desenvolvimento

## Antes de codar

Leia:
- docs/PROJECT.md
- docs/ARCHITECTURE.md
- docs/BUSINESS-RULES.md

## Ordem recomendada

### Fase 0 — Fundação
Monorepo, tooling, Docker, Prisma, CI, apps vazios e documentação.

### Fase 1 — Identidade
Usuários, autenticação e permissões.

### Fase 2 — Catálogo
Produtos, categorias e códigos de barras.

### Fase 3 — Localização
Hierarquia de localização e QR Codes.

### Fase 4 — Estoque
Estoque por localização e transações.

### Fase 5 — Armazenamento
Tarefa -> escaneamento -> validação -> confirmação -> auditoria.

### Fase 6 — Consulta
Busca por nome/SKU/barcode e visualização da localização.

### Fase 7 — Inventário
Conferência por localização e divergências.

## Critério

Cada fase deve deixar o projeto executável, testável e com documentação atualizada.

Não criar um monólito gigante de código em uma única etapa.
