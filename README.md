<div  Align="justify">
<div Align="center"><img src="https://github.com/R-FlyD/RFlyD/assets/56831082/4682303c-0db2-4e00-af20-d37f0bf44366" width=700 height=400> </div>

# Sumario
- [Objetivo do Trabalho](#Objetivo-do-Trabalho)
- [Funcionamento](#Funcionamento)
- [Mode de Execução](#Mode-de-Execucao)
- [Hardware](#Hardware)
  - [RDM6300](#RDM6300)
  - [ACS712-30A](#ACS712-30A)
  - [Drone](#Drone)
  - [Carregador Indução](#Carregador-Inducao)
  - [Modulo Desenvolvido](#Modulo-Desenvolvido)
- [Software](#Software)
  - [Node-red](#Node-red)
  - [Banco de Dados](#Banco-de-Dados)
  - [Site](#Site)
  - [Simulação](#Simulacao)

# <a name=“Objetivo-do-Trabalho”><a/>Objetivo do Trabalho
A automatização do processo de inventário em armazéns é uma necessidade para garantir a eficiência e a precisão dos estoques. A discrepância entre o sistema virtual e a quantidade física de estoque é um problema comum nas empresas, mas pode ser resolvido com o uso de tecnologias como a identificação por radiofrequência (RFID). A utilização de drones equipados com essa tecnologia permite uma identificação mais rápida, precisa e eficiente dos produtos, além de oferecer vantagens em termos de rapidez, precisão e redução de custos em comparação com outros métodos de catalogação. Com a adoção da automatização do processo de inventário, é possível aumentar a eficiência logística, garantir a satisfação do cliente e melhorar a gestão de recursos.

A **RFlyD** traz uma tem como objetivo a integração de drone, RFID e site proprío para gestão autônomo de um inventario.
# <a name=“Funcionamento”><a/>Funcionamento
Nosso sistema opera com um drone equipado com um módulo que possui um circuito capaz de executar a leitura de tags RFID. Essas tags são lidas por uma antena própria desenvolvida pela nossa equipe, juntamente com um módulo industrial RDM6300, responsável pelo tratamento do sinal. Por meio da ESP (placa de desenvolvimento), exibimos o valor da tag. Posteriormente, a ESP se encarrega de enviar o código da tag via MQTT para o Node-RED, instalado localmente em um computador que compartilha a mesma rede da ESP.

No Node-RED, realizamos uma verificação para determinar se a tag possui cadastro no banco de dados local e, em seguida, alteramos a variável de checagem da tag para "true". Isso permite mostrar no site que a tag foi lida com sucesso. Com essa solução integrada, garantimos um processo eficiente e preciso de leitura de tags RFID e o registro adequado das informações em nosso sistema.

# <a name=“Mode-de-Execucao”><a/>Mode de Execução
Para executar o projeto como um todo, primeiro é preciso ter executado a instalação correta de todos os repositorios sitados neste readme, sendo eles **([Node-red](https://github.com/R-FlyD/Node-red); [RFID-MQTT](https://github.com/R-FlyD/RFID-MQTT)
; [SITE](https://github.com/R-FlyD/SITE); [Simulacao](https://github.com/R-FlyD/Simulacao))**. Posteriormente ligue o site seguindo as instruções em [Site](#Site), reconfigure a ssid e a senha do wifi no codigo da esp em [Modulo Desenvolvido](#Modulo-Desenvolvido), e com isso você sera capaz de ler as tags e verificar suas alterações no site.

# <a name=“Hardware”><a/>Hardware
## <a name=“RDM6300”><a/>RDM6300
Implementação pode ser analisada em 
> https://github.com/R-FlyD/RDM6300-Continuo

## <a name=“ACS712-30A”><a/>ACS712 30A
Implementação pode ser analisada em 
> https://github.com/R-FlyD/-ACS712-NodeMCU-12E

## <a name=“Drone”><a/>Drone
## <a name=“Carregador-Inducao”><a/>Carregador Indução
## <a name=“Modulo-Desenvolvido”><a/>Modulo Desenvolvido
https://github.com/R-FlyD/RFID-MQTT

# <a name=“Software”><a/>Software
## <a name=“Node-red”><a/>Node-red
<div><img src="https://cdn.xingosoftware.com/elektor/images/fetch/dpr_1/https%3A%2F%2Fwww.elektormagazine.com%2Fassets%2Fupload%2Fimages%2F42%2F20200612144414_Node-Red-official-logo.png" width=250> </div>

Implementação pode ser analisada em 
> https://github.com/R-FlyD/Node-red

## <a name=“Banco-de-Dados”><a/>Banco de Dados




## <a name=“Site”><a/>Site
Implementação pode ser analisada em 
> https://github.com/R-FlyD/SITE

## <a name=“Simulacao”><a/>Simulação
Implementação pode ser analisada em 
> https://github.com/R-FlyD/Simulacao

# Autores
| [<img src="https://avatars.githubusercontent.com/u/56831082?v=4" width=115><br><sub>Arthur Coelho Estevão</sub>](https://github.com/arthurcoelho442) |  [<img src="https://avatars.githubusercontent.com/u/56406192?v=4" width=115><br><sub>Milena da Silva Mantovanelli</sub>](https://github.com/Milena0899) |
| :---: | :---: |

</div>
