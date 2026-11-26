# Validação experimental do DAGP

Plano de validação 0.1.0-draft. Os jogos são atividades de referência, não componentes normativos do protocolo. Nenhum ensaio foi executado ainda.

## Progressão

| ID | Atividade | Foco incremental |
|---|---|---|
| VAL-001 | Porrinha | Associação, governança, commit-reveal, sincronização |
| VAL-002 | Dominó | Embaralhamento em camadas, distribuição seletiva, auditoria, LDV |
| VAL-003 | Pife | Compra, descarte, transferência e proteção de objetos |
| VAL-004 | Sobrevivendo na Ilha | Aleatoriedade coletiva, recursos e proposições concorrentes |
| VAL-005 | FPS Battle Royale | Escalabilidade, latência e eventos verificáveis |

## VAL-001 — Porrinha

Modalidade proposta: três palitos iniciais por jogador; mão secreta de zero até o saldo; palpites distintos em ordem rotativa; acerto elimina um palito; primeiro a zerar vence. Número de participantes definido pela atividade.

Fluxo: descobrir candidatos; constituir sala; comprometer mãos com hash de contexto, quantidade e nonce secreto; fechar compromissos; registrar palpites; revelar mãos; verificar compromissos; consolidar soma e resultado; repetir ou encerrar.

Ensaios: partida normal, empate sem acerto, palpite duplicado ou fora do intervalo, revelação incompatível, omissão, replay de rodada anterior, mensagens duplicadas e fora de ordem, desconexão e recuperação de histórico. Política inicial proposta para omissão: derrota por abandono e anulação da rodada afetada; formalizar antes de implementar.

Aceite: hosts honestos convergem para mesmo estado e resultado em condições suportadas; mãos não são divulgadas pelo protocolo antes da fase de revelação; ações inválidas não alteram estado; falhas fora das hipóteses de segurança são explicitadas.

### Perfis de associação

- Nativo: descoberta direta por portas universais (números e transporte pendentes).
- PWA online: Gateway para descoberta e sinalização WebRTC DataChannel.
- PWA offline: aplicação previamente disponível offline, sinalização manual por QR Code (oferta/resposta e candidatos ICE necessários), sem depender de STUN/TURN externos; testar conectividade direta na WLAN. Conexões existentes podem encaminhar sinalização autenticada para novos pares sem adquirir autoridade. Não presumir que toda WLAN permita comunicação entre clientes.
- Após constituição, Gateway dispensável para conexões diretas estabelecidas. Reconexão pode exigir nova sinalização. Testar desligamento do Gateway e da internet separadamente, isolamento de clientes e suspensão do navegador.
- Malha completa: n(n-1)/2 conexões; quatro hosts exigem seis. QR pode exigir fragmentação conforme tamanho da sinalização.

Aceite específico offline: demonstrar partida completa em celulares Android na mesma WLAN sem internet, registrar navegador, versão, topologia e falhas. Se não houver caminho direto, declarar associação indisponível; não usar relay oculto como evidência de conexão direta.

## VAL-002 — Dominó

Constituir sala; embaralhar peças em camadas independentes; comprometer permutações; distribuir objetos opacos; solicitar diretamente chaves intermediárias autorizadas; jogar peças mediante proposições; auditar quando previsto.

Ensaios: duplicação/substituição de peças, compromisso incompatível, pedido de chave alheia, omissão de embaralhador, recuperação seletiva LDV com uma e duas camadas, ausência de guardião, depósito inválido e auditoria que comprometa sigilo. Aceite: inventário preservado, abertura seletiva conforme construção escolhida, recuperação ou falha explícita, sem reivindicar segurança contra conluio não demonstrada.

## VAL-003 — Pife

Reutilizar embaralhamento e distribuição; governar compra, descarte, posse e revelação de combinações. Testar compra concorrente do mesmo objeto, descarte inválido, transferência sem acesso prévio, consulta a registros de chaves e novo embaralhamento para romper associação anterior. Aceite: nenhuma dupla atribuição finalizada nas condições suportadas; conhecimento anterior não é tratado como revogável.

## VAL-004 — Sobrevivendo na Ilha

Atividade de referência com recursos, ações simultâneas e eventos aleatórios. Regras específicas ainda pendentes. Testar commit-reveal de aleatoriedade com reservas previamente comprometidas, acumulação de revelações válidas, omissão e exclusão, esgotamento de reservas/quórum, disputa por recurso, ações incompatíveis, deliberações derivadas e recuperação. Sombra agendada opcional. Aceite: resultados reproduzíveis e convergentes, falha explícita quando requisitos não forem satisfeitos.

## VAL-005 — FPS Battle Royale

Investigar limites, não presumir viabilidade de governança por evento de alta frequência. Definir quais eventos exigem decisão coletiva e quais são simulação local; regras e modelo de verificação pendentes. Medir latência, jitter, tráfego, CPU, memória, crescimento da malha, divergência de estado e impacto de perda/partição. Aceite exploratório: identificar envelope operacional e gargalos, sem prometer desempenho competitivo ou prevenção de trapaças.

## Registro comum de ensaio

Registrar ID, versão/commit, configuração, regras, perfil de transporte, quantidade de hosts, dispositivos, condições de rede, hipóteses de confiança, cenário, resultado esperado/observado, evidências, latência, bytes/mensagens, CPU/memória e status (não executado, aprovado, reprovado, bloqueado). Separar testes locais simulados, integração real e adversariais. Não confundir aprovação funcional com prova criptográfica. Limiares quantitativos serão definidos por atividade antes do aceite correspondente.

## Implementação

Começar com núcleo de referência e Porrinha em examples/porrinha/ (proposta), JavaScript e simulação local de quatro hosts, depois WebRTC real. Manter regras dos jogos separadas do núcleo. Os demais exemplos serão incrementais. Não há código executável nem resultados nesta seção.
