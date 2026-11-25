# DAGP 0.1.0-draft — especificação central

Estado experimental: decisões conceituais, não requisitos completos de interoperabilidade. propostas em aberto não são garantias.

## Princípios
1. Organização delegável: descoberta pode ser auxiliada por Gateway.
2. Constituição consensual: membros reconhecem a mesma composição e regras.
3. Governança indelegável: decisões são apuradas pelos próprios participantes.
4. Autonomia operacional: a sala não depende do Gateway após constituída.
5. Ausência de confiança prévia: identidade criptográfica não implica honestidade.

A atividade define número de participantes, requisitos de proximidade, regras, estado, prazos, quóruns (respeitando mínimos universais ainda a formalizar), conflitos e sanções. DAGP não implementa regras de jogos. Não exige blockchain.

## Camadas
Transporte; descoberta; associação; segurança; sincronia; governança; aplicação. Ferramentas opcionais de compromisso, aleatoriedade, embaralhamento, distribuição e custódia complementam o núcleo.

## Fluxo
Descobrir candidatos → validar diretamente → constituir sala → deliberar e executar → recuperar lacunas ou reconciliar divergências. O encerramento é definido pela atividade.

## Contrato da atividade (conceitual)
Manifesto identifica atividade e versão de regras, critérios de ingresso, cardinalidade, proposições admissíveis, opções de resposta, critérios de decisão, limites de profundidade e prazo, política de recuperação e sanções. Todos devem reconhecer a mesma versão antes de iniciar. Formato serializado pendente.

Ver [associação](spec/association.md), [governança](spec/governance.md), [sincronia](spec/synchronization.md) e [ferramentas](tools/README.md).
