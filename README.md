# Política de privacidade — CameraBridge

Última atualização: 12 de novembro de 2026.

O CameraBridge é mantido por Magno Souza / Magnuvo Software. Contato para dúvidas e solicitações sobre dados: [@the.magno no Instagram](https://www.instagram.com/the.magno/). Esta política se aplica ao aplicativo Android, ao cadastro de testadores e à API de diagnósticos do CameraBridge.

## Câmera, arquivos e funcionamento local

O aplicativo usa Bluetooth e Wi-Fi para se comunicar com câmeras e importar arquivos para o telefone. As permissões de dispositivos próximos, rede, notificações e armazenamento, quando necessárias, servem a essas funções. Vídeos, fotos, áudio, GPS, força G e outros sensores gravados nas mídias são processados localmente. Essas mídias e seus dados de localização não são enviados à API de diagnósticos. O aplicativo não exige conta para importar ou visualizar mídias e não inclui anúncios ou ferramentas de publicidade.

O desenvolvimento tem como foco câmeras HERO5 ou mais novas. Modelos anteriores estão fora do escopo de suporte. A lista de modelos distingue funções testadas em hardware, integração ainda não testada e ausência de suporte; a existência de documentação de uma câmera não garante seu funcionamento no aplicativo.

As galerias de mídias na câmera e de arquivos já importados são separadas. Os originais são preservados sem recompressão; a exportação H.264 gera uma cópia local e pode incorporar recorte e mostradores dos sensores. Dados auxiliares de GPS, sensores, miniaturas, LRV/THM e WAV associados podem ficar no armazenamento privado do aplicativo. A exclusão de um vídeo pelo app também remove os auxiliares locais associados; a verificação na abertura limpa auxiliares sem vídeo correspondente. Transferências e exportações iniciadas pelo usuário podem continuar em segundo plano com uma notificação de progresso, respeitando as limitações do Android.

As credenciais Wi-Fi obtidas da câmera ou informadas pelo usuário são usadas durante a conexão; o CameraBridge não as inclui no catálogo nem nos relatórios. Ao compartilhar ou arrastar uma mídia baixada para outro aplicativo, o usuário entrega esse arquivo ao destino escolhido, que passa a tratá-lo conforme sua própria política. O CameraBridge não envia o arquivo à sua API para realizar esse compartilhamento.

Consultas de atualização de firmware, quando solicitadas ou habilitadas, acessam o site oficial da GoPro usando o modelo da câmera. O botão de contato abre o Instagram em um aplicativo ou navegador externo. Esses serviços têm suas próprias políticas de privacidade.

## Cadastro voluntário para testes

Na distribuição pelo Drive, o usuário pode informar voluntariamente o e-mail da conta que usa na Google Play para pedir participação nos testes. Enviamos esse e-mail por HTTPS à API do CameraBridge e armazenamos temporariamente o endereço, seu hash, a data do cadastro e o status de inclusão na lista de testadores. Enquanto a inclusão está pendente, conservamos o e-mail para permitir adicioná-lo à lista. Após a confirmação de inclusão na Google Play, apagamos o endereço em texto e mantemos somente seu SHA-256, status e datas. Nas consultas seguintes, normalizamos o e-mail informado (espaços externos removidos e letras minúsculas), calculamos o SHA-256 e verificamos tanto cadastros pendentes pelo endereço quanto registros pelo hash, sem voltar a guardar o endereço de quem já foi incluído. O hash permite correlação e tentativas de reconhecimento de endereços conhecidos; é pseudonimização, não anonimato garantido.

O e-mail serve para administrar o programa de testes e, quando o responsável efetivar a inclusão, poderá ser informado ao Google Play. Cadastrar-se no aplicativo não significa inclusão automática na Play Store. O link de teste depende da liberação da versão e da autorização da conta pelo Google Play. Não associamos a tabela de e-mails aos relatórios de dispositivos.

A versão destinada à Play Store não inclui o formulário de cadastro. As cópias de testes têm validade fixa desde sua geração: 14 dias na distribuição Play e 30 dias na distribuição Drive. O aviso de expiração orienta a atualização; na cópia Drive, permite acessar o cadastro de testadores. A validade não obriga a aceitar diagnósticos.

## Diagnósticos opcionais de compatibilidade

Nas novas instalações desta versão, os diagnósticos opcionais ficam desligados e não há aviso ao abrir o aplicativo. Você pode ativá-los em Privacidade e diagnósticos, onde são explicados os dados, a finalidade e os controles antes de confirmar a opção. Uma escolha feita anteriormente é respeitada: uma atualização não ativa quem havia desativado, nem desativa automaticamente quem já havia autorizado. Versões anteriores podiam apresentar uma escolha na primeira abertura. Nenhum relatório é transmitido em uma instalação nova antes da ativação pelo usuário. Você pode desativar a qualquer momento em Privacidade e diagnósticos, interrompendo novos envios, e pode solicitar a exclusão dos relatórios desta instalação. Quando autorizado, o aplicativo pode enviar relatórios técnicos de sucesso e falha da comunicação, para entendermos quais modelos funcionam e corrigirmos problemas. O usuário também pode solicitar o envio pela área de diagnósticos.

Quando autorizado, o aplicativo guarda uma fila privada de relatórios ainda não confirmados pelo servidor, inclusive sem internet. A fila é limitada a 256 relatórios e 2 MiB; registros mais antigos podem ser descartados para não ocupar espaço indefinidamente. Registros com eventos fora do prazo de 30 dias são descartados quando a fila é processada. Os envios usam lotes gzip menores que 500.000 bytes, com tentativa a cada 45 segundos enquanto o processo está ativo. Em segundo plano, um trabalho de rede do Android pode tentar novamente sem notificação; o sistema pode adiar ou suspender essa execução. Não garantimos o recebimento de todos os registros ou um intervalo exato quando o app estiver suspenso ou encerrado. Falhas de envio permanecem silenciosas, sem avisos de erro. Ao desativar os diagnósticos, cancelamos os envios e descartamos a fila local; relatórios anteriores à nova autorização não voltam a ser enviados. Isso não apaga os relatórios já recebidos pelo servidor.

Os relatórios podem conter:

- Versão do aplicativo, canal de distribuição, modelo do smartphone e versão do Android.
- Identificador aleatório de cada relatório, usado para distinguir envios e evitar a duplicação da mesma requisição.
- Modelo da câmera, quando identificado.
- Identificador pseudonimizado do smartphone, derivado de um identificador restrito ao contexto do aplicativo; não lemos IMEI, número de telefone ou serial físico protegido do Android.
- Identificador pseudonimizado derivado do serial da câmera; o serial em texto não é enviado nesse campo.
- Horários dos eventos, etapas da conexão, códigos de resposta/erro, tipos de exceção e caminhos técnicos previamente permitidos. Os nomes dos arquivos são removidos desses caminhos.

Esses identificadores permitem reconhecer relatórios do mesmo dispositivo no contexto do app. Portanto, os dados são **pseudonimizados e não devem ser descritos como totalmente anônimos**. Reinstalar, mudar de pacote ou de assinatura pode alterar a identificação do telefone. Não existe identificação garantida entre todas as instalações e canais.

O identificador do relatório é diferente do identificador do smartphone: um telefone pode enviar vários relatórios. Não usamos esses identificadores para descobrir o nome ou a conta Google da pessoa, nem os vinculamos ao e-mail do cadastro de testadores. O canal Play/Drive/Development descreve a compilação executada, não comprova por qual loja ou link o arquivo foi instalado. A API atual não coleta o nome do instalador. Execuções em emuladores ou testes automatizados também podem gerar relatórios, quando a opção for confirmada nesse ambiente; um relatório, por si só, não comprova a presença de um usuário humano ou de uma câmera física. Antes de identificar a câmera na tentativa de conexão, os campos referentes à câmera podem ficar vazios.

Não incluímos nos relatórios vídeos, fotos, áudio, trilhas GPS, valores dos sensores das mídias, nomes de arquivos, conteúdo de mensagens de exceção, senha ou nome da rede Wi-Fi, credenciais Bluetooth, e-mail do cadastro ou identificadores de publicidade. O esquema do servidor aceita apenas os campos técnicos previstos; esses relatórios não são uma cópia irrestrita dos logs do telefone.

## Servidor, proteção e retenção

O cadastro e os relatórios são enviados por HTTPS para a API do CameraBridge em infraestrutura administrada pelo responsável pelo aplicativo. Os dados ficam em banco MariaDB com acesso restrito ao serviço e à administração autorizada. Não vendemos esses dados e não os usamos para publicidade. O Google Play recebe os endereços que o responsável efetivamente adicionar ao programa de testes; os provedores de infraestrutura processam os dados necessários à hospedagem e ao transporte.

O endereço IP é necessariamente processado na conexão e pode ser usado temporariamente em memória para limitar abusos. Não o incluímos nas tabelas de diagnóstico/cadastro. Os endpoints do CameraBridge não registram corpos das requisições nem mantêm log de acesso HTTP próprio contendo esses dados. Falhas operacionais graves da infraestrutura podem gerar registros técnicos separados.

Os relatórios de diagnóstico são conservados por até 30 dias, com limpeza na inicialização e a cada hora; a execução dessa limpeza pode acrescentar até uma hora ao prazo. Todos os registros da tabela de testadores, inclusive e-mails pendentes e hashes, serão apagados 30 dias após o lançamento público na Play Store, ou quando o projeto for descontinuado, o que ocorrer primeiro. O teste interno não inicia esse prazo. O responsável registra a data do lançamento público ou a descontinuação no servidor. Após o encerramento, o cadastro e as consultas de testadores ficam indisponíveis e não recriam registros; a limpeza também roda periodicamente, em até uma hora, e na inicialização. A exclusão nesta API não remove a lista administrada pelo Google Play; o Google tem sua própria política de retenção. Não prometemos disponibilidade permanente do serviço.

## Controle e exclusão

Você pode desativar os diagnósticos nas configurações do aplicativo para interromper novos envios e descartar a fila local. Isso não apaga automaticamente relatórios já enviados: use a opção de excluir os relatórios deste dispositivo, enquanto o identificador da instalação ainda estiver disponível. Sem essa instalação, ou para solicitar acesso, correção ou exclusão do cadastro de e-mail, entre em contato com [@the.magno](https://www.instagram.com/the.magno/), informando a solicitação. Podemos pedir informações proporcionais para confirmar que o pedido se refere aos seus dados.

Excluir uma mídia local apaga seus auxiliares locais conforme a função do app; isso não equivale à exclusão dos relatórios do servidor. A exclusão de mídia da câmera é uma ação separada e exige confirmação no aplicativo.

## Alterações

Esta política será atualizada quando o tratamento de dados mudar. A versão vigente ficará disponível no repositório público de privacidade e no endereço HTTPS de privacidade do CameraBridge. Mudanças não autorizam coletar dados adicionais sem a informação e o consentimento aplicáveis no aplicativo.

