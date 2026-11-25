# Governança, deliberação e comunicação

Proposições fechadas apresentam intenção e opções conforme regras compartilhadas. Podem expressar ação objetiva (cada host verifica a admissibilidade independentemente) ou decisão subjetiva. Respostas conceituais: ACCEPT, DENY, INVALID, INCONCLUSIVE; ausência de resposta é condição distinta. Argumentos e evidências estruturados podem originar proposições derivadas até consenso ou votação. A atividade define opções, conflitos, consequências e limites.

## Índices
Cada ação possui identificador sala:host:contador monotônico por origem; não há contador global para emissão. Proposições derivadas referenciam parent_id e root_id e incluem depth. Mensagens e decisões precisam de identificação própria e vínculo à ação; numeração de decisão e ordem de aplicação ainda exigem definição. Assinaturas e representação canônica pendentes. Duplicatas devem ser idempotentes; mesmo identificador com conteúdos diferentes é evidência de equivocações.

## Deliberação
Proposições concorrentes são permitidas; a atividade resolve conflitos. Limite de profundidade e prazo impedem espera ilimitada. Ausentes não contam como votos; maioria dos respondentes é a intenção operacional, condicionada ao quórum e perfil de segurança. Uma maioria local não garante finalização segura sob partição. Certificados de decisão, quóruns intersectantes e regra de finalização são pendências. Não consolidar decisões incompatíveis até resolvê-las.

## Ausência
Registrar ausência e recuperar histórico no retorno. A atividade decide sanções, sem presumir intenção maliciosa a partir de timeout.

## Sombra agendada (extensão experimental)
Para atividades simples, representação determinística de agente ausente pode ser previamente distribuída em forma protegida; remanescentes concordam com abertura, executam a mesma representação e contabilizam uma única ação/voto lógico. Não é regra geral nem garante imparcialidade; custódia e autorização pendentes.
