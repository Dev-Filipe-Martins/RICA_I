# Redes Industriais para Controle e Automação
## Material de estudo para apresentação do Trabalho Final

### Definição de Rede:
Rede é um grupo de computadores conectados por um meio de comunicação de dados de forma a compartilhar recusos.

Os meios de comunicação pode ser:
- (Bluetooth) Rede Pessoal: Possui uma distancia de aproximadamente 1m entre o cliente e o servidor.
- (LAN - Local area network) Rede Local: A distancia entre o cliente e o servidor pode variar de 10m a 1Km.
- (MAN - Metropolitan area network) Rede Metropolitana: Distancia entre 10Km.
- (WAN - Wide-Area Network) Redes Geograficamente Distribuída: Faixa de distancia entre 100Km e 1000Km.
Uma WAN é um conjunto de LAN's ou outras redes que se comunicam ente si. A WAN é essencialmente a rede das redes.
- Internet: Cobre uma distancia na casa de 10.000Km.
A Internet é a maior rede Wan existente.

### IP (Internet Protocol):
É o protocolo do grupo TCP/Ip (Transmission Control Protocol/Internet Protocol) responsável pela identificação de redes e dos dispositivos conectados a elas, como: 
computadores, servidores, impressoras, roteadores, celulares, tablets, etc.

#### IPV4 (Internet Protocol versão 4):
O IPV4 é um protocolo responsavel por identificar dispositivos de internet.

Utiliza números de 32 bits para identificar cada dispositivo. 

É composto por quatro números (Octetos) de 0 a 255, separados por pontos.

Exemplo:

    192.168.122.123

Ao receber um número IP, o dispositivo passa a ser identificado na rede e torna-se um anfitrião (Host)

#### DHCP (Dynamic Host Configuration Protocol) - IP Dinamico
DHCP atribui endereços IP automaticamente a computadores e dispositivos.

#### Classes de Rede:
- Classe A: Rede grande, poucos hosts - O primeiro octeto definia a rede e os demais os hosts. Endereços de classe A abrangem um grande número de redes, mas com pouca quantidade de dispositivos por rede.
- Classe B: Rede média, número médio de hosts - Os dois primeiros octetos definiam a rede e os demais os hosts. Endereços de classe B possibilitam um número moderado de redes (cerca de 16 mil redes) e um número razoável de dispositivos por rede (até 65 mil por rede).
- Classe C: Rede pequena, muitos hosts - Os três primeiros octetos definiam a rede e o último os hosts. Endereços de classe C fornecem uma grande quantidade de redes (mais de 2 milhões), porém com um número limitado de dispositivos por rede (até 254 por rede).

### Protocolo ICMP (Internet Control Message Protocol):
É um mecanismo usado por hosts e gateways para enviar notificações de problemas ocorridos com datagramas de volta ao emissor.

O ICMP funciona como um mensageiro, enviando informações de erro e controle entre dispositivos em uma rede IP.

### CSMA (Carrier Sense Multiple Access):
É um método de acesso a meio compartilhado utilizado em redes com um único canal de comunicação, como cabos Ethernet ou redes sem fio iniciais.

### VLAN (Virtual Local Area Network):
É uma técnica usada para criar segmentos virtuais dentro de uma rede física local (LAN).

As VLAN's usam tags especiais adicionadas aos pacotes de dados para identificar a qual VLAN eles pertencem.

Switches de rede VLAN são responsáveis por roteamento e gerenciamento do tráfego entre as VLANs.

Switches VLAN podem filtrar o tráfego com base na tag VLAN, permitindo comunicação apenas entre dispositivos na mesma VLAN ou definindo regras específicas para comunicação entre VLANs diferentes.

#### Pode ter mais de uma VLAN na mesma porta?
Sim, é possível ter várias VLANs em uma mesma porta de um switch, desde que o switch seja um switch gerenciado e suporte a trunk.

No caso do Trabalho final é possivel ter varias VLAN's:
- VLAN 1
- VLAN 10
- VLAN 20
- VLAN 30
- VLAN 40

#### Como funciona um Trunk?
O Trunk funciona como um canal agrupado que permite a transmissão simultânea do tráfego de várias VLANs através de um único link físico (cabo de rede). 

Imagine um rodovia com várias pistas separadas. O trunk seria como uma rodovia onde diversos veículos (dados de VLANs diferentes) trafegam ao mesmo tempo, mas cada um em sua própria pista (identificada por tags) evitando colisões.

O processo de comunicação com Trunk é feito da seguinte maneira:
- Um dispositivo conectado a uma VLAN específica envia seus pacotes de dados.
- O switch de acesso identifica a qual VLAN o dispositivo pertence e adiciona uma tag de cabeçalho ao pacote de dados. Essa tag identifica a VLAN de origem.
- O switch encapsula o pacote de dados da VLAN com o cabeçalho de trunking de acordo com o protocolo utilizado.
- O pacote encapsulado, contendo os dados da VLAN e a tag de trunking, é transmitido através do cabo de rede do link trunk.
- O switch de destino no outro extremo do link trunk recebe o pacote encapsulado.
- O switch de destino reconhece o cabeçalho de trunking e extrai o pacote de dados original. Usando a tag VLAN contida no pacote, o switch encaminha os dados para a porta apropriada conectada à VLAN de destino.
- O dispositivo final na VLAN de destino recebe os pacotes de dados originalmente enviados pelo dispositivo na outra VLAN.

#### STP(Spanning Tree Protocol):
É um protocolo crucial utilizado em redes Ethernet comutadas para prevenir loops (caminhos fechados) e garantir a conectividade livre de erros. Funciona como um sistema inteligente de tráfego que elimina esses loops na rede.

#### EtherChannel:
É uma tecnologia usada em switches Cisco para agregar vários links Ethernet físicos em um único canal lógico de alta performance. Possibilitando um tráfego de dados muito mais rápido e eficiente.

O EtherChannel combina a largura de banda de todos os links físicos agregados, proporcionando uma conexão mais veloz para transferir grandes volumes de dados.

#### A comunicação entre um ponto e outro é possivel? Porque?
É possível, mas com algumas condições:
- Deve haver um caminho físico entre os dispositivos que desejam se comunicar, passando pelos switches de acesso e chegando ao switch core. Isso significa que os cabos de rede devem estar conectados corretamente entre os switches e os dispositivos.
- O switch core precisa estar configurado para rotear o tráfego entre as VLANs. Isso significa que ele deve ter as interfaces VLANs configuradas com endereços IP e rotas apropriadas para cada VLAN.
- Para que dispositivos em diferentes VLANs se comuniquem, eles precisam ter endereços IP na mesma sub-rede e o roteador (switch core) configurado para encaminhar os pacotes entre as VLANs.

### APIPA(Automatic Private IP Addressing):
É um recurso que permite que um dispositivo atribua automaticamente a si mesmo um endereço IP e uma máscara de sub-rede caso não consiga obtê-los de um servidor DHCP.

É um mecanismo de backup que ajuda os dispositivos a funcionarem em uma rede local mesmo sem um servidor DHCP. No entanto, não substitui um servidor DHCP configurado corretamente ou um endereçamento IP estático para funcionalidade completa de rede.

