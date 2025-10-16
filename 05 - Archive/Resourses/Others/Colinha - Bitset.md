---
tags:
  - unicap
  - maratona
---

#### Operadores sobre Bits
###### Operador AND
| Variável  | Val | Representação em Bits |
| --------- | --- | --------------------- |
| a         | 5   | 0000010**1**          |
| b         | 9   | 0000100**1**          |
| a **&** b | 1   | 0000000**1**          |
| c         | 10  | 0000**1**010          |
| d         | 12  | 0000**1**100          |
| c **&** d | 8   | 0000**1**000          |
_exemplo de uso: Com o operador `&`, podemos verificar se um número `n` é par usando `n & 1`_
###### Operador OR inclusivo
| Variável   | Val | Representação em Bits |
| ---------- | --- | --------------------- |
| a          | 5   | 00000**1**0**1**      |
| b          | 9   | 0000**1**00**1**      |
| a **\|** b | 13  | 0000**11**0**1**      |
| c          | 10  | 0000**1**0**1**0      |
| d          | 12  | 0000**11**00          |
| c **\|** d | 14  | 0000**111**0          |
###### Operador OR exclusivo
| Variável  | Val | Representação em Bits |
| --------- | --- | --------------------- |
| a         | 5   | 00000**1**0**1**      |
| b         | 9   | 0000**1**00**1**      |
| a **^** b | 12  | 0000**11**00          |
| c         | 10  | 0000**1**0**1**0      |
| d         | 12  | 0000**11**00          |
| c **^** d | 6   | 00000**11**0          |
###### Operador NOT
| Variável | Val | Representação em Bits               |
| -------- | --- | ----------------------------------- |
| a        | 5   | 00000000 00000000 00000000 00000101 |
| **~**a   | -6  | 11111111 11111111 11111111 11111010 |

_A fórmula `~x = -x - 1` é válida. Por exemplo, `~5 = 6`._
###### Operador de deslocamento à esquerda
_Desloca os bits do primeiro operando à esquerda pelo número de bits especificado pelo segundo operando (deve ser um valor positivo): preenche a partir da direita com zero (0)._ 

| Variável       | Val | Representação em Bits |
| -------------- | --- | --------------------- |
| a              | 1   | 0000000**1**          |
| a = a **<<** 1 | 2   | 000000**1**0          |
| a = a **<<** 1 | 4   | 00000**1**00          |
| a = a **<<** 1 | 8   | 0000**1**000          |
| b              | 7   | 00000**111**          |
| b **<<=** 3    | 56  | 00**111**000          |
###### Operador de deslocamento à direita
_Desloca os bits do primeiro operando à direita pelo número de bits especificado pelo segundo operando (deve ser um valor positivo): preenche a partir da esquerda com zero (0)._

| Variável       | Val | Representação em Bits |
| -------------- | --- | --------------------- |
| a              | 8   | 0000**1**000          |
| a = a **>>** 1 | 4   | 00000**1**00          |
| a = a **>>** 1 | 2   | 000000**1**0          |
| a = a **>>** 1 | 1   | 0000000**1**          |
| b              | 56  | 00**111**000          |
| b **>>=** 3    | 7   | 00000**111**          |
###### Aplicações
_Um número da forma `1 << k` tem um bit na posição `k` e todos os outros bits são zero, então esse número pode ser usado para acessar bits únicos de números. Em particular, o k-ésimo bit de um número é 1 exatamente quando `x & (1 << k)` não é zero. Por exemplo, para imprimir a representação de bits de um número `int` pode ser usado o seguinte código:_
```c++
for(int i = 31; i >= 0; i--){
    if(x&(1<<i)){ cout << "1"; }
    else{ cout << "0"; } 
}
```
- `x = x | (1 << k)`: define o k-ésimo bit de `x` para 1;
- `x = x & ~(1 << k)`: define o k-ésimo bit de `x` para 0;
- `x = x ^ (1 << k)`: inverte o k-ésimo bit de `x`;
- `x = x & (x − 1)`: define o último bit 1 de `x` como zero;
- `x = x & −x`: define todos os bits 1 como 0, exceto o último bit 1;
- `x = x | (x − 1)`: inverte todos os bits após o último bit 1;
- `x & (x − 1)`: se `x` for um número positivo, verifica se `x` é uma potência de dois.

#### Bitset
```c++
#include <bitset>
using namespace std;

bitset<SIZE> nome;
bitset<8> bset1(10);     // 00001010
bitset<8> bset2(string("1010")); // 00001010 
bitset[i];               // acessa o bit
bitset.count();          // retorna o número de bits ligados
bitset.size();           // retorna o tamanho
bitset.test();           // retorna o bit na posição 
bitset.all();            // retorna true se todos estão ligados
bitset.any();            // retorna true se algum está ligado
bitset.none();           // retorna true se nenhum está ligado
bitset.reset();          // desliga o bit (desliga todos se não determinar qual bit)
bitset.set();            // liga o bit (liga todos se não determinar qual bit)
bitset.flip();           // troca o bit (troca todos se não determinar qual bit)
bitset.to_string();      // converte para string
```


