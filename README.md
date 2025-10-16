📂 #Projeto: Route on a Stick - VLANs e Roteamento Inter-VLAN


Este projeto demonstra a configuração de roteamento inter-VLAN utilizando a técnica Route on a Stick em um ambiente de rede com dois switches (SW1 e SW2) e um roteador (Router01). O exercício inclui criação de VLANs, configuração de trunks, VTP, subinterfaces do roteador com encapsulamento 802.1Q e IP Helper para comunicação entre VLANs e servidores DHCP.

Objetivo do Projeto:

Configurar múltiplas VLANs (SRV, ADM e TI) em switches.

Implementar o roteamento inter-VLAN utilizando um único link físico do roteador (Route on a Stick).

Garantir que cada VLAN tenha seu gateway e que o tráfego entre VLANs seja roteado corretamente.

Demonstrar conhecimentos em VTP (server e client), trunks e subinterfaces do roteador.

Tecnologias / Comandos Utilizados:

Cisco IOS

VLANs (10, 20, 30)

VTP Server/Client

Trunking (802.1Q)

Subinterfaces no roteador

IP Helper-Address (DHCP relay)

