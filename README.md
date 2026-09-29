# Stocky

Sistema interno de localização e movimentação de estoque para loja de materiais de construção.

## Objetivo

O Stocky permite consultar exatamente onde um produto está e orientar o estoquista a armazenar produtos no local correto, validando fisicamente a localização por QR Code.

## Princípios

- Simplicidade para o funcionário.
- PostgreSQL como fonte de verdade.
- Produto + localização + movimentação sempre auditáveis.
- QR Code utilizado para validar a localização física.
- O mapa/3D é uma representação da localização, não a fonte de verdade.

## Status

Projeto em fase de especificação e fundação.

## Aplicações

- `apps/web`: aplicativo para computador/administração.
- `apps/mobile`: aplicativo para celular/operação.
- `apps/api`: backend.

## Documentação

Consulte `docs/` antes de implementar funcionalidades.
