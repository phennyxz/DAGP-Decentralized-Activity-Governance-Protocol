# Descoberta, qualificação e constituição

O host mantém lista local de candidaturas com atividade, identidade e chave pública. Procura Gateway quando disponível e permitido; sem ele, hosts nativos poderão descobrir pares por portas universais (duas ou três, números pendentes). Navegadores não escutam portas arbitrárias; perfil web usa Gateway e transporte entre pares, por exemplo WebRTC. NAT, sinalização e TURN exigem política explícita: perfil estritamente direto exclui conexões que necessitem retransmissão.

## Mural
Gateway mantém mural dinâmico por atividade, sem dono, enquanto houver candidato. Host consulta, assina atualizações e copia a lista; apresenta-se diretamente aos candidatos, que confirmam interesse e identidade. Gateway verifica interesse e remove candidaturas negativas, expiradas ou já integradas. Não integra sala, não recebe chaves privadas nem governa. Após início da constituição, novos candidatos aguardam a próxima sala no mesmo mural.

## Qualificação
Proximidade virtual significa visibilidade, alcançabilidade e resposta apropriada. Atividade pode exigir número, latência de rede, resposta correta a desafio dentro de prazo e outros requisitos. Primeiros candidatos que satisfazem requisitos têm preferência; não se procura indefinidamente uma solução ótima.

## Eleição condicional
Quando houver competição simultânea por vagas, cada host ordena candidatos aprovados conforme ordem local de satisfação e divulga tabela assinada. Todos calculam a média das posições sobre o mesmo conjunto de tabelas e selecionam os melhores elegíveis. Não há segundo voto obrigatório. Negociação criptográfica confirma composição e regras. Empates, ausência de tabelas, conjuntos divergentes, limites de rodada e equivocações precisam de regras determinísticas antes da implementação. Sem competição, não há eleição necessária.

## Constituição
Confirmação comum da lista de membros, identificador de sala e manifesto. Identidade, autenticação, negociação de chaves e prova de posse pendentes em nível de wire protocol. Gateway é dispensável após a formação.
