
**BOLD**
*italic*

`codigo inlinne`

```kotlin
```
#
##
###
####

<p align="center">     
 <img width="600" height="180" src="">
 </p> 

# Basic
## Part 1 - Intro to Qlik Sense
## Part 2 - Understanding The Data Modeling User Interfaces

### Certification Lecture Qlik Sense 
* Misto de decoreba com prática;  
* Pensar com cabeça qlik, pensar self service;  
Estudo de casos: Pensar passo a passo no script, desenhar na mão  

**EXEMPLO DE QUESTÃO:**
Join de tabelas = se tem join sem campo em comum chave, gera produto cartesiano; 
OBESERVAR A GRAFIA DOS CAMPOS CHAVES PARA VER SE É CHAVE

**EXEMPLO DE QUESTÃO:**  
Resident de uma tabela = se dar resident de uma tabela e usar exatamente os mesmos campos, você terá um autoconcatenate.  
Se a tabela tem 10 linhas, passará a ter 20, e terá apenas 1 tabela.  
SOLUÇÃO = noconcatenate  e drop da tabela temporária
POREM = enquanto o resident é dado com no concatenate, há uma chave syntética de todos campos.  
PROBLEMA = Quando um campo é chave, ele não pertence a nenumha tabela mais, mas as duas.  

**EXEMPLO DE QUESTÃO**  
De onde vem esse valor? qual tabela posso apagar?  

**EXEMPLO DE QUESTÃO**   
Se eu der resident em uma tabela e não nomear ela, qual o nome da tabela? o nome original da tabela que foi feito o resident.  
SEMPRE OBSERVAR NOMES DE TABELAS PARA NÃO CAIR EM PEGADINHAS
Pode ser que o load final esteja chamando uma tabela que não existe!

PAREI EM 45 MIN - 04/06/2019

**DATAS**  
Sempre converter quando extrair datas de conexões ou salvar em qvd com num(). Quando extrair é importante para padronizar, e quando salvar é importante para otimizar a carga.
* DATE# : quando o parâmetro recebeido é texto. O outro quando é num.



