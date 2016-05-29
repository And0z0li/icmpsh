## Cenário

O ICMP não tem pacotes pré-definidos para envia-los, todos os pacotes são criados pelo S.O, o que permite que muitos pacotes sejam forjados. Utilido deste codigo para o desenvilvimento de meu TCC, que trata exatamente sobre como pequenos descuidos como este pode gerar grandes problemas.
Agradecimentos ao Nico e ao Bernardo que inicialmente criaram este código fantastico.

## Descrição

Este código inicialmente necessitava da interação dos dois lados para iniciar a troca de pacotes ICMP, com pequenos ajustes fiz com que este se tornasse um backdoor, sendo capaz de se instalar no computador da vitima, enviar informações de endereço IP e se manter ativo ate a reinicialização do sistema.

Tudo aqui mencionado foi desenvolido exclusivamente para o TCC de meu curso em Redes de Computadores.


## Uso

### Executando o Mestre

Para executar o mestre é necessario algumas bibliotecas, são elas:

* IO::Socket
* NetPacket::IP
* NetPacket::ICMP

E para que o mestre consiga responder aos chamados do escravo, é necessario desabilitar o não envio de respostas ICMP contido nos sistemas Linux

```
sysctl -w net.ipv4.icmp_echo_ignore_all=1
```

Caso não execute o comando acima, não recebera as requisições do escravo

### Executando o escravo

Para executar o escravo é necessario antes fazer uma pequena alteração

```
Na linha 179 é necessario inserir seu endereço IP

OBS: Caso esteja abaixo de um NAT é necessario utilizar algum programa que mantenha seu IP ativo na internet
