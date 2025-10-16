 ### 📂 Projeto: Route on a Stick - VLANs e Roteamento Inter-VLAN


Este projeto demonstra a configuração de roteamento inter-VLAN utilizando a técnica Route on a Stick em um ambiente de rede com dois switches (SW1 e SW2) e um roteador (Router01). O exercício inclui criação de VLANs, configuração de trunks, VTP, subinterfaces do roteador com encapsulamento 802.1Q e IP Helper para comunicação entre VLANs e servidores DHCP.

### Objetivo do Projeto:
- Configurar múltiplas VLANs (SRV, ADM e TI) em switches.
- Implementar o roteamento inter-VLAN utilizando um único link físico do roteador (Route on a Stick).
- Garantir que cada VLAN tenha seu gateway e que o tráfego entre VLANs seja roteado corretamente.
- Demonstrar conhecimentos em VTP (server e client), trunks e subinterfaces do roteador.

---
### Configurações dos Dispositivos:

### Configuração SW1 (Switch Server)

**enable**
**conf t**
**vlan 10**
**name SRV**
**vlan 20**
**name ADM**
**vlan 30**
**name TI**
**exit**
**vtp mode server**
**vtp domain cisco**
**vtp password cisco
**int fa 0/1**
**sw acc vl 10**
**exit**
**int rang fa 0/2-9**
**sw acc vl 20**
**exit**
****int rang fa 0/10-19
**sw acc vl 30
**exit
**int range gi 0/1-2**
**sw mo trunk**
**sw trunk all vlan all**
**exit**

### Configuração SW2 (Switch Client)
**enable**
**conf t**
**vtp mode client**
**vtp domain cisco**
**vtp password cisco**
**int rang fa 0/1-9**
**sw acc vl 20**
**exit**
**int rang fa 0/10-19**
**sw acc vl 30**
**exit**
**int range gi 0/1-2**
**sw mo trunk**
**sw trunk all vlan all**
**exit**

### Configuração Router01 (Roteamento Inter-VLAN)
**enable**
**conf t**
**int gi 0/0/0**
**no shut**
**exit**
**int gi 0/0/0.10**
**description #####VLAN SRV#####**
**enca dot1q 10**
**ip add 192.168.1.1 255.255.255.0**
**ip helper-address 192.168.1.10**
**exit**
**int gi 0/0/0.20**
**description #####VLAN ADM#####**
**enca dot1q 20**
**ip add 192.168.10.1 255.255.255.0**
**ip helper-address 192.168.1.10**
**exit**
**int gi 0/0/0.30**
**description #####VLAN SRV#####**
**enca dot1q 30**
**ip add 192.168.20.1 255.255.255.0**
**ip helper-address 192.168.1.10**
**exit**

### Resumo das VLANs e IPs

| VLAN | Nome | Gateway      |
| ---- | ---- | ------------ |
| 10   | SRV  | 192.168.1.1  |
| 20   | ADM  | 192.168.10.1 |
| 30   | TI   | 192.168.20.1 |


