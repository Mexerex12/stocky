# Stocky — Regras de Negócio

## RN-001 — Localização estruturada
Uma localização é uma entidade e pode possuir uma localização pai.

## RN-002 — Produto pode ter múltiplas localizações
Não assumir uma única localização por SKU.

## RN-003 — Consulta exata
A consulta deve mostrar quantidade e endereço físico legível.

## RN-004 — Validação de armazenamento
Uma tarefa de armazenamento normal deve validar o produto e a localização física antes da confirmação.

## RN-005 — QR incorreto
Se o QR escaneado não corresponder ao destino esperado, a confirmação normal deve ser bloqueada.

## RN-006 — Histórico
Movimentações não devem ser apagadas ou sobrescritas para corrigir histórico.

## RN-007 — Auditoria
Alterações sensíveis devem registrar usuário e data/hora.

## RN-008 — Capacidade
Uma localização pode possuir restrições de peso, volume ou capacidade.

## RN-009 — Linguagem operacional
A interface operacional deve priorizar nomes humanos de locais em vez de IDs técnicos.

## RN-010 — 3D não é fonte de verdade
Coordenadas 3D nunca substituem a localização de domínio.

## RN-011 — Divergências
Divergências devem permanecer registradas até tratamento explícito.

## RN-012 — Concorrência
O backend deve prevenir confirmações inconsistentes quando duas operações tentarem alterar o mesmo estoque simultaneamente.
