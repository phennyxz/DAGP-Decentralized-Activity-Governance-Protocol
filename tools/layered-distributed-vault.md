# LDV — Layered Distributed Vault

Estado: desenho conceitual do DAGP 0.1.0-draft. Nome técnico provisório. LDV compõe criptografia e distribuição de segredos existentes; não é uma nova primitiva criptográfica.

## Objetivo
Permitir recuperação cooperativa de um segredo de um host indisponível sem conceder a um único guardião acesso antecipado. Aplicável a chaves intermediárias de embaralhamento, reservas de aleatoriedade e representação de sombra agendada. A atividade define quando recuperar, quantas camadas exigir e consequências de indisponibilidade.

## Construção
O titular A escolhe n >= 1 chaves independentes de alta entropia. Para segredo S, define C0=S e Ci=AEAD_Encrypt(Ki, nonce_i, C(i-1), contexto_i), para i de 1 a n. Distribui Cn a um guardião e cada Ki a um guardião distinto, todos diferentes de A. Nonces e metadados necessários à abertura acompanham a respectiva camada. Usar canais privados autenticados; suíte, codificação e parâmetros exatos pendentes.

Exemplo com duas camadas:
- B recebe C2 = Enc(K2, Enc(K1,S)).
- C recebe K1.
- D recebe K2.
- A conserva o segredo original.
- Recuperação: D permite remover camada externa, C permite remover interna, mediante cooperação com B.

São n+1 guardiões para n camadas e pelo menos n+2 hosts contando o titular. Não há limiar k-de-m nesta modalidade: todos os componentes são necessários. O titular já conhece o segredo.

## Constituição e registro
Antes de depender do cofre, titular identifica sala, finalidade, objeto, versão, guardiões e camadas. Vincula criptograficamente os componentes a esse contexto, publica manifesto assinado e compromisso do ciphertext, e obtém recibos autenticados de custódia. Recibos comprovam declaração de recebimento, não que o segredo original seja correto ou recuperável. Não publicar hashes de segredos de baixa entropia sem proteção. Atribuição cíclica é opção, não obrigação. A atividade pode rejeitar configuração com membros insuficientes.

## Recuperação
1. Detectar indisponibilidade conforme política da atividade; timeout não prova má-fé.
2. Propor recuperação identificando cofre, versão, objeto, destinatário autorizado e finalidade.
3. Obter decisão válida da governança; guardiões verificam autorização e contexto antes de cooperar.
4. Fornecer ciphertext e material de abertura por canais autenticados e privados ao destinatário autorizado, ou remover camadas sucessivamente sob política equivalente.
5. Verificar autenticação de cada camada e integridade do objeto recuperado; quando aplicável, conferir compromisso anterior do segredo.
6. Registrar resultado e recibos sem publicar chaves ou plaintext. Se faltar componente ou autenticação falhar, declarar recuperação malsucedida e aplicar regra da atividade.

Não há obrigação de transmitir chaves à sala inteira. Recuperação de chave de peça deve ser limitada ao destinatário autorizado. Uma decisão de governança não impede tecnicamente guardiões em conluio de cooperarem fora do protocolo.

## Granularidade e ciclo de vida
Preferir cofres por objeto ou unidade de revelação quando abrir um lote inteiro comprometer sigilo. Não reutilizar chaves de recuperação entre cofres independentes. Mudanças de guardião, titularidade ou versão exigem nova configuração e recibos antes de abandonar a anterior. Rotação não apaga conhecimento já adquirido nem cópias antigas; expiração e descarte são políticas, não garantias de apagamento remoto.

## Segurança e disponibilidade
Com n chaves independentes e um ciphertext mantido exclusivamente pelo guardião designado, a abertura por terceiros exige cooperação dos n+1 guardiões, sob hipótese de criptografia segura e ausência de vazamentos. Se ciphertext se tornar público, somente os n guardiões de chaves são necessários. Qualquer guardião indispensável pode impedir recuperação. Mais camadas aumentam custo de conluio sob essas hipóteses, mas diminuem disponibilidade. Um titular malicioso pode depositar material inválido; recibos e AEAD não provam consistência com segredo usado na atividade. Verificação de depósito, redundância, VSS e recuperação por limiar são extensões futuras, não requisitos da modalidade básica.

## Integração
LDV é ferramenta de recuperação de segredos, não substitui embaralhamento, distribuição seletiva ou governança. A transferência de posse é uma proposição da atividade. Quando o titular anterior não deve conhecer o objeto, consultar registros de fornecimento de chaves; ausência de registro não prova ausência de acesso clandestino. Quando pode conhecer conteúdo mas não deve reconhecer sua representação posterior, realizar novo embaralhamento de conjunto indistinguível com proteção renovada e ao menos uma transformação secreta inacessível ao antigo titular.

## Testes previstos
- Recuperação com uma e duas camadas e todos os guardiões.
- Falha com componente ausente, chave incorreta, ciphertext adulterado, versão antiga ou contexto divergente.
- Rejeição de pedido não autorizado e destinatário incorreto.
- Isolamento entre cofres de objetos diferentes.
- Simulação de desconexão, conluio, depósito inválido e recuperação parcial.
- Medição de armazenamento, tráfego, latência e custo por camada.

Não implementado nem auditado. A segurança da governança e do transporte permanece dependência do núcleo DAGP.
