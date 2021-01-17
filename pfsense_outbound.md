Buenas galera, tudo tranquilo?

Recentemente nosso provedor nos informou que havia criado filtros de conexões tcp originarias do nosso GW ponto-a-ponto com eles. O pfsense utiliza esse GW como source IP em sua busca por pacotes e atualizações e dessa forma estava sendo bloqueado esse acesso.

Após muita pesquisa e conversando com amigos, consegui resolver.

Como utilizamos IP plublico em nossas vlans, consigo utilizar a saida de uma delas.

## Procedimentos:

No pfsense navegue ate **Firewall** > **NAT** > **Port Forward** e crie uma regra como mostro na imagem abaixo:

![PFSENES!](https://eliasmoraispereira.files.wordpress.com/2016/10/9b369-outbound_vlan.png?w=300)

## Detalhamento:

*   Interface: wan
*   Protocol: any
*   Source:
    *   Type: Network
    *   Address:
*   Destination: any
*   Translation:
    *   Address: Other Subnet
    *   Other Subnet:
    *   Pool Options: Round Robin

Após tudo isso clique em **Save** and voilá!!! Agora seu pfsense está buscando novamente as atualizações!!
