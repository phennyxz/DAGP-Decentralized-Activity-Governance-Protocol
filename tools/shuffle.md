# Embaralhamento distribuído auditável e distribuição seletiva

Cada embaralhador recebe lista X, aplica transformação criptográfica reversível por objeto e permutação secreta, produz Y e transmite ao próximo. Camadas independentes (cores) protegem objetos; não exigir mudança de ordem como condição de aleatoriedade, pois a identidade pode ocorrer legitimamente. Identificadores de objetos e cardinalidade devem ser preservados.

## Compromisso Bias
Antes de transformar, embaralhador compromete Bias secreto de alta entropia. Para cada par entrada/saída publica compromisso h_i = H(encode(contexto, X_i, Y_pi(i), Bias)). Exemplo ilustrativo X=abcdefg, Y=3541276, sete compromissos. O Bias não deve ser um deslocamento pequeno enumerável; a transformação criptográfica efetiva e as chaves são elementos distintos a definir. Listas e conjunto de compromissos devem ser vinculados à rodada e assinados.

Em contestação, abrir compromisso do Bias, mapeamento e dados/chaves necessários à validação da transformação. Auditor verifica bijeção, cardinalidade, ausência de substituição e compatibilidade com todos os compromissos. Hash isolado não demonstra transformação legítima nem aleatoriedade. Auditoria é posterior, não prova de validade antes de uso. Revelar segredos pode expor camada inteira; atividade decide auditoria imediata com invalidação, ou após partida e consequências. Recusa de abertura deve ser tratada.

## Distribuição
A atividade governa atribuição de objetos opacos a destinatários. Destinatário solicita diretamente a cada embaralhador intermediário apenas material de abertura das peças atribuídas (ex.: sete peças por cor no dominó). Respostas autenticadas e privadas; validar autorização e não entregar chaves de objetos alheios. Material por peça não deve permitir abrir outras peças. Encadeamento de referências entre camadas deve evitar revelar mapeamento global. A construção de cifras, rastreamento privado, distribuição e recuperação de chaves ainda não está especificada; não afirmar sigilo ou resistência a conluio antes de análise. Provas de conhecimento zero podem constituir modalidade futura, não exigência da modalidade auditável inicial.
