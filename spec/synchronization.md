# Sincronização e recuperação

DAGP registra proposições, respostas, evidências e decisões, não impõe modelo de estado da atividade. Distinguir dados públicos, privados e comprometidos. Não retransmitir segredos indiscriminadamente.

## Recuperação incremental
Comparar índices por origem e solicitar lacunas específicas. Exemplo: A:003, A:004, C:005. Contadores detectam perda, não estabelecem ordem global. Hashes de histórico e replay de decisões auxiliam identificação de divergência; a atividade define ordem e aplicação de efeitos.

## Reconciliação completa
Host dessincronizado solicita históricos de decisões a todos os membros. Verifica integridade e assinaturas, compara cópias e agrupa as coincidentes; afasta progressivamente variantes mais singulares até atingir o limiar acordado. Não destrói evidências divergentes. Se não houver acordo suficiente, consulta validade das decisões em ordem, da primeira à última divergência relevante, e utiliza a própria governança para reconciliar. Em caso de impasse, suspender consolidação conflitante.

O limiar depende da atividade. Deve existir mínimo universal de corroboração, cujo valor ainda precisa ser ratificado; dois históricos distintos coincidentes e três como padrão foram propostas, não decisão definitiva. Atividades de dois membros necessitam perfil próprio com decisões assinadas e reconciliação bilateral. Cópias coincidentes não provam legitimidade perante conluio. Quóruns e finalização durante partições permanecem em aberto.
