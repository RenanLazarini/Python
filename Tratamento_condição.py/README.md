Este código respeita a LGPD e não compromete nenhum dado sensível.

Este script foi desenvolvido para otimizar uma etapa real do processo de atualização
de uma base de Onboarding.

Antes da automação, essa etapa era realizada manualmente e levava, no mínimo,
cerca de 40 minutos para ser concluída. Dependendo do tamanho da base de disparo
do Onboarding, esse tempo podia ser ainda maior.

Com a implementação do tratamento em Pandas, o tempo de execução passou a ser
de aproximadamente 2 segundos.

A lógica aplicada no código replica fielmente o processo de interpretação manual,
avaliando cada um dos campos de condição e a combinação entre eles. A partir disso,
é definido o valor correto para cada ID presente na planilha.

Ao final do processo, o arquivo já tratado é gerado automaticamente.
