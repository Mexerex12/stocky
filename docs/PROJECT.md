# Stocky — Projeto

## 1. Visão

O Stocky é um sistema interno para controlar localização física, estoque e movimentações de produtos em uma loja de materiais de construção.

O sistema deve responder rapidamente a duas perguntas:

1. Onde está exatamente este produto?
2. Onde este produto deve ser armazenado?

## 2. Usuários

### Vendedor
Consulta estoque e localização. Não movimenta estoque.

### Estoquista
Consulta produtos, executa armazenamentos, retiradas e inventários.

### Separador
Executa tarefas de separação e consulta localizações.

### Gerente
Acompanha operação, divergências, inventário e configurações operacionais.

### Administrador
Gerencia usuários, produtos, localizações, regras e configurações globais.

### Auditor
Executa conferências e consulta histórico/auditoria.

## 3. Aplicativos

### Web
Uso em computador para administração e consulta.

Principais áreas:
- Dashboard
- Estoque
- Produtos
- Localizações
- Mapa
- Movimentações
- Inventário
- Tarefas
- Usuários
- Configurações

### Mobile
Uso operacional no depósito/loja.

Ações principais:
- Localizar produto
- Guardar produto
- Retirar produto
- Conferir estoque
- Minhas tarefas
- Mapa

## 4. Localização

A localização física deve ser modelada como uma hierarquia flexível, usando relação pai/filho:

Loja > Área > Setor > Corredor > Estante > Módulo > Prateleira > Posição

A estrutura não deve depender de uma string única. Cada nó é uma entidade própria e pode possuir um `parentId`.

A aplicação deve exibir endereços em linguagem humana. Identificadores internos não devem ser a interface principal para funcionários.

## 5. QR Codes

Cada localização operacional que precise de confirmação física deverá possuir um QR Code único.

O QR identifica a localização física no sistema.

O QR não deve, por si só, ser considerado prova de movimentação: a movimentação só é concluída após as regras de validação do fluxo.

## 6. Produtos

Um produto pode possuir:
- SKU
- nome
- categoria
- um ou mais códigos de barras
- unidade de estoque
- peso
- dimensões
- volume, quando aplicável

O mesmo produto pode existir em mais de uma localização simultaneamente.

## 7. Estoque por localização

A quantidade deve ser armazenada por produto e localização.

Exemplo:

Produto X: 37 unidades totais
- Local A: 25
- Local B: 12

A quantidade total é derivada das quantidades por localização e das demais regras do domínio.

## 8. Movimentações

Toda movimentação relevante deve preservar:
- produto
- quantidade
- origem
- destino
- usuário responsável
- data/hora
- motivo/tipo
- referência da tarefa, quando houver

Não sobrescrever histórico.

## 9. Fluxo de consulta

1. Usuário pesquisa por nome, SKU ou código de barras.
2. Sistema encontra o produto.
3. Sistema mostra quantidade total.
4. Sistema mostra uma ou mais localizações.
5. Usuário pode abrir mapa ou iniciar orientação.

## 10. Fluxo de armazenamento

1. Estoquista inicia "Guardar produto".
2. Escaneia o código de barras do produto.
3. Sistema identifica o produto e a quantidade/tarefa.
4. Sistema determina o destino recomendado conforme as regras cadastradas.
5. Estoquista vai até o local.
6. Estoquista escaneia o QR Code da localização.
7. Sistema compara a localização escaneada com a localização esperada.
8. Se estiver correta, permite confirmação.
9. Ao confirmar, registra a movimentação e atualiza o estoque.
10. Se estiver incorreta, bloqueia a confirmação normal e mostra o local esperado.

## 11. Exceções de armazenamento

O sistema deve tratar, entre outras:
- QR incorreto
- produto incorreto
- localização sem capacidade
- produto sem localização compatível
- necessidade de destino alternativo
- ausência de conectividade
- tarefa duplicada/conflitante

As exceções devem gerar estado auditável e não devem ser resolvidas silenciosamente.

## 12. Inventário

O usuário pode escanear uma localização e conferir fisicamente os itens esperados.

Divergências precisam ser registradas sem apagar o valor esperado.

## 13. Mapa

Primeira versão: mapa 2D simples.

Fase posterior: modelo 3D com coordenadas associadas às entidades de localização.

A localização do banco permanece como fonte de verdade; o mapa apenas representa essa localização.

## 14. Escopo inicial

Prioridade do MVP:
1. Fundação do monorepo
2. Autenticação e perfis
3. Produtos e códigos de barras
4. Localizações e hierarquia
5. Estoque por localização
6. QR Codes
7. Consulta
8. Armazenamento validado
9. Movimentações e auditoria
10. Inventário básico

Fora do MVP inicial:
- AR
- IA de slotting
- ERP
- 3D avançado
- roteirização sofisticada
- previsão de demanda

Esses itens podem ser adicionados posteriormente sem alterar a fonte de verdade do domínio.
