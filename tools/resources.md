# Transferência de posse e custódia

A posse é governada pela atividade, não exige ferramenta criptográfica independente. Registrar objeto opaco e titular, transferência e consumo como proposições. Transferências conflitantes não podem finalizar simultaneamente; depende de finalização segura do núcleo.

## Transferência e conhecimento
- Se A não deveria conhecer o objeto transferido a B, B consulta registros autenticados de fornecimento de chaves intermediárias. Ausência de registros não prova ausência de conluio ou acesso clandestino.
- Se A pode continuar reconhecendo o objeto, basta transferência governada e autorização de revelação seletiva a B.
- Se A conhecia conteúdo mas não deve reconhecer sua representação, B inicia novo embaralhamento de conjunto de objetos indistinguíveis com proteções renovadas e transformação secreta inacessível a A. Não é possível revogar conhecimento já adquirido.

## Custódia
Camadas de embaralhamento constituem custódia distribuída. Para indisponibilidade de titular de segredo, utilizar [LDV](layered-distributed-vault.md), com cofre criptografado e chaves separados entre guardiões. Recuperação por limiar (SSS/VSS) é extensão futura opcional, não requisito básico.
