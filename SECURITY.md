# Segurança — estado experimental

DAGP não possui prova formal, implementação auditada nem garantia de consenso bizantino. Zero trust é princípio, não certificação. Ameaças: identidades Sybil, equivocação, replay, partições, conluio, omissão seletiva, comprometimento de chaves, manipulação de listas e vazamento por auditoria.

Pendências obrigatórias antes de perfil interoperável: identidade e autenticação; assinatura e serialização canônica com separação de domínios; confidencialidade de canais; negociação e rotação de chaves; acordo sobre membros, transcritos e rodadas; quóruns intersectantes e finalização; ordenação de decisões conflitantes; limites de recursos; construção criptográfica de embaralhamento e abertura seletiva. Definir pressupostos de rede e tolerância a falhas por perfil. Não usar em atividades de alto risco ou valor real enquanto não avaliadas.

Relate vulnerabilidades sem publicar segredos ou dados pessoais; canal privado de reporte ainda não definido.

## Literatura de referência para avaliação futura
- SoK: Distributed Randomness Beacons, https://eprint.iacr.org/2023/728 (commit-reveal e último revelador).
- Good things come to those who wait, https://eprint.iacr.org/2024/1711 (recuperação de contribuições).
- Secure and practical constant round mental poker, https://doi.org/10.1016/j.ins.2014.02.151 (verificação de embaralhamento).
