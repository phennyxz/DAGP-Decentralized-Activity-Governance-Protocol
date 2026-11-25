# Compromisso e aleatoriedade coletiva

Commit-reveal: publicar C = H(encode(contexto, valor, nonce)) antes da abertura. Contexto vincula sala, ação, participante, finalidade e rodada; nonce secreto de alta entropia impede enumeração quando o valor tem domínio pequeno (porrinha: 0 a 3). Ao abrir, verificar compromisso. Codificação canônica e suíte criptográfica ainda pendentes.

## Aleatoriedade acumulativa com contingência (desenho acordado)
Antes de revelar qualquer valor, cada host compromete contribuição principal e reservas independentes para rodadas limitadas. Congelar conjunto de participantes e compromissos. Revelar principais; verificar e acumular todas as contribuições válidas. Se houver omissão, não consolidar o resultado parcial: excluir omissos das rodadas seguintes, registrar ocorrência e acionar reservas dos remanescentes. Somar/combinar reservas válidas ao acumulado original, nunca substituir o acumulado. Nova omissão aciona nova reserva enquanto houver quórum e reservas. Finalizar somente em rodada sem omissões e com requisitos satisfeitos; caso contrário declarar falha explícita.

Uma contribuição honesta ainda desconhecida torna o resultado complementar imprevisível para quem omitiu anteriormente. Valores não precisam ser distintos. Exemplo didático: 17+32+24=73, D omite 15; reservas válidas 13+28+41 adicionam 82, acumulado 155. A saída mapeada pode inclusive coincidir com aquela que D tentou evitar. Usar alta entropia e derivação criptográfica com ordenação canônica e amostragem sem viés; fórmula final pendente.

O protocolo registra não revelação, não intenção. Atividade escolhe penalidade desde redução de indicador até derrota. A técnica não garante imparcialidade absoluta sob conluio, abortos seletivos, esgotamento de reservas ou falhas de acordo sobre o transcript. Custódia verificável é alternativa futura para recuperação de contribuições.
