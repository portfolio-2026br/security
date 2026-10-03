# Sempre Vigilante

É uma prática muito sensata acompanhar se sua configuração de hardware e software está segura e o quê os robôs da
internet conseguiram garimpar sobre você, sua família, sua empresa, ...

Neste texto eu demonstro que esta prática pode resultar em achados muito interessantes, curiosos, e até, perturbadores!

## Índice

<img align="right" src="../images/Atento.png" width="128" height="128" alt="Vigilante logo">

1. [Pesquise Sempre](#pesquise-sempre)
2. [Exploits](#exploits)
   1. [Root shell exploit para Xiaomi routers](#root-shell-exploit-para-xiaomi-routers)
3. [Agradecimentos e Créditos](#agradecimentos-e-créditos)
4. [Conclusão](#conclusão)

## Pesquise sempre

Em algum momento (do passado) a plataforma Lattes divulgava muita informação para quem tinha currículo lá. O `Escavador`
aproveitou esta brecha, importou e mantinha um PDF com excesso de informações a meu respeito. Eu apaguei meu currículo
Lattes e, usando a LGPD, solicitei que meus dados fossem apagados no `Escavador`.

O IFSP ainda mantém um PDF com meu CPF disponível para acesso público. Quando você se inscreve em algum processo
seletivo é razoável esperar que a publicação dos resultados precise divulgar informações. Mas, divulgar meu CPF
inteirinho, sem obfuscar nenhuma parte em um site de acesso público na internet não é demais? Eu vou esperar mais algum
tempo e vou reclamar. A bandidagem ganhou, sem custo, a informação que aquela sequência de números é um CPF válido e
ativo; sem trabalho e sem esforço!

## Exploits

Em [outro texto neste repositório](../hack-linux/README.md) eu já descrevi um evento em que um software muito usado
continha em presentinho amargo. Aqui vou descrever um exploit de `root` que se aplica a vários roteadores Xiami.

### Root shell exploit para Xiaomi routers

Primeiro ponto a destacar é que, no passado, embora eu tivesse um roteador TP-LINK disponível, eu decidi comprar um novo
roteador pois eu sabia na época que o TP-LINK não recebia mais atualições e tinha falhas de segurança conhecidas no
submundo.

Na realidade, apesar de mostrar a você que meu roteador tem uma brecha séria de segurança, eu ainda recomendo os
roteadores Xiami para mim e para outros pois:

- o produto oferece bom preço e bom hardware;
- meu modelo oferece a possibilidade de substituir o software OEM por OpenWRT;
- portanto, eu consigo resolver o problema e manter meu roteadore atualizado hoje e por mais alguns anos (algo MUITO
  raro neste mercado).

Dito isto, vamos ver o sangue jorrar na tela:

#### O exploit

Basta descobrir o que fazer. Obtive sucesso na primeira tentativa:

![Ataque com sucesso](images/OS%201.png)

#### Uma vez feito, a CLI é toda sua

Eu acessei usando `telnet` e executei comandos de meu interesse:

![Evidência 1](images/OS%202.png)

![Evidência 2](images/OS%203.png)

![Evidência 3](images/OS%204.png)

#### Mas ainda tem mais

Bom, todos os produtos fazem isto. Ainda assim, é bom saber que o router manda um alô para casa (usando o meu IP para
isto, é claro). O meu IP vai permitir obter a geolocalização, entre outros detalhes. Mas, vamos analisar os logs do
roteador:

![Saudade de casa 1](images/Saudades%201.png)

Quem será que está na escuta?

![Saudade de casa 2](images/Saudades%202.png)

## Agradecimentos e créditos

A vulnerabilidade foi descoberta por Andrés Cecilia Luque.

## Conclusão

Você precisa, ao menos, estar ciente das "peculiaridades" do hardware e software que você tem em casa. Feito isto, você
pode mitigar e/ou acompanhar os riscos e as possíveis consequências.

Ao avaliar as imagens acima nós percebemos que para explorar a falha um atacante precisaria conhecer a senha do roteador
e estar na mesma rede que eu, o que torna desafiador para um atacante externo explorar esta falha.

Mesmo assim, boas práticas como substituir a "senha de fábrica" por uma senha forte é novamente a primeira sugestão.

PS: aliás, você sabia que é fácil identificar dispositivos que possuem senhas padrão e que estão expostos na Internet
usando mecanismos de busca como o Shodan (<https://www.shodan.io>)?
