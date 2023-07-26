<div  Align="justify">
<div Align="center"><img src="https://github.com/R-FlyD/RFlyD/assets/56831082/9b7f2e37-66d9-40da-b360-5ee7a08c8319" width=300> </div>

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
O drone utilizado para o projeto foi comprado levando em consideração o custo mais acessivel do mercado, o drone escolhido foi o drone Eachine E88 Pro que é um quadricóptero de tamanho compacto, projetado para ser portátil e fácil de transportar. Possui duas câmera HD integrada que permite capturar vídeos e fotos aéreas. O E88 Pro vem com recursos de voo estáveis, como o modo de altitude hold, e também pode ser controlado via aplicativo de smartphone.

<div Align="center"><img src="https://github.com/R-FlyD/RFlyD/assets/56831082/4f361a29-2a9b-4527-bf5f-7c57ab234175" width=250> </div>

## <a name=“Carregador-Inducao”><a/>Carregador Indução
O carregador por indução desenvolvido foi elaborado com base em um reator de lâmpada fluorescente e no modelo de antena desenvolvido, composto por um solenoide de duas camadas, cada uma contendo 20 espiras, totalizando 40 espiras no conjunto.

<div Align="center"><img src="https://github.com/R-FlyD/RFlyD/assets/56831082/4cf0ce8d-3dcd-4e63-b9e9-70c2a97a62b8" width=250> </div>

## <a name=“Modulo-Desenvolvido”><a/>Modulo Desenvolvido
Implementação pode ser analisada em 
> https://github.com/R-FlyD/RFID-MQTT

# <a name=“Software”><a/>Software
## <a name=“Node-red”><a/>Node-red
<div><img src="https://cdn.xingosoftware.com/elektor/images/fetch/dpr_1/https%3A%2F%2Fwww.elektormagazine.com%2Fassets%2Fupload%2Fimages%2F42%2F20200612144414_Node-Red-official-logo.png" width=250> </div>

Implementação pode ser analisada em 
> https://github.com/R-FlyD/Node-red

## <a name=“Banco-de-Dados”><a/>Banco de Dados
<div><img src="https://github.com/R-FlyD/RFlyD/assets/56831082/fbfcca45-bd4d-4405-b08d-188f5f134ef8" width=250> </div>

O banco de dados desenvolvido se deu na utilização do banco de dados PostgreSQL , com a criação de 4 tabelas no banco *control*, *historic*, *product* e *product_identification*, como mostrado na imgem abaixo:

<div align="center"><img src="https://github.com/R-FlyD/RFlyD/assets/56831082/8b8e1c89-c9e3-4a11-a325-fe2aded8f099" width=550> </div>

O banco de dados desenvolvido foi projetado para garantir uma gestão eficiente e precisa dos estoques no armazém. A tabela *product* permite manter um cadastro completo dos produtos armazenados, incluindo informações relevantes como o tipo de produto, seu custo, nome e descrição. Além disso, a associação de uma imagem do produto facilita a identificação visual e auxilia na organização do espaço.

Por outro lado, a tabela *product_identification* possui uma chave estrangeira para product e serve para identificar embalagens presentes no armazém. Como várias caixas podem conter o mesmo produto, o *product_identification* permite diferenciá-las através de um código RFID único para cada uma. Além disso, essa tabela possui um atributo booleano chamado checked, que é utilizado para que o drone saiba se uma caixa foi ou não catalogada.

A inserção da tabela *historic* no banco de dados fornece um acompanhamento detalhado das atividades no armazém. Essa tabela registra a data e o local onde cada caixa foi colocada, permitindo uma visualização detalhada do histórico de movimentação ao longo do tempo. Isso possibilita o rastreamento das caixas em diferentes momentos e locais dentro do armazém, o que é essencial para uma logística mais eficiente e uma gestão precisa dos recursos disponíveis.

Além das tabelas mencionadas anteriormente, também foi utilizada a tabela *control*, que desempenha um papel importante ao possibilitar a escolha da funcionalidade da antena presente no hardware. Por meio dessa tabela, é possível definir se a antena funcionará como um carregador (True), utilizando o carregamento por indução, ou como um leitor RFID (False), para identificar e rastrear as caixas presentes no armazém.

Ao combinar essas tabelas em um banco de dados PostgreSQL, a equipe responsável pelo armazém ganha maior controle e visibilidade sobre o estoque, o que resulta em uma operação mais eficiente e uma melhor experiência para os clientes. A automatização do processo de inventário, impulsionada pelas tecnologias como a identificação por radiofrequência (RFID) e a utilização de drones, contribui para a redução de custos, otimização do tempo e aumento da satisfação dos clientes. O banco de dados desenvolvido se torna ainda mais completo com a inclusão da tabela control, integrando todas as funcionalidades necessárias para uma gestão eficiente e precisa dos estoques.

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
