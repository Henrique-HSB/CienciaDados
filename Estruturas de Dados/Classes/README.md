
# Classes  
## Noções Básicas 
A unidade básica da POO é a classe, que encapsula atributos estáticos e comportamento dinâmicos em uma caixa.
A classe é um modelo usado para criar objetos, também chamados de instâncias. A comunicação com os objetos é feita pelo uso da interface pública do objeto. 
A complexidade envolvida na realização de uma tarefa fica escondida dentro da classe. Uma vantagem do paradigma é o isolamento, quando alterações não afetam todo o sistema.
Esse isolamento facilita a adição de novas funcionalidades e correção de problemas. Como os detalhes de implementação ficam escondidos dentro da classe, podemos gerar implementações diferentes facilmente. 
Em Estruturas de Dados, isso permitirá separar a visão lógica, da visão de implementação e da visão de aplicação. A visão lógica de uma classe será sempre criada em um arquivo de extensão .h. 
Nesse arquivo, definiremos os membros públicos e privados de uma classe. A implementação da classe será sempre feita em um arquivo de extensão .cpp. 
O arquivo .cpp deverá sempre importar o arquivo .h com a diretiva include. É comum tentar incluir uma definição de classes mais de uma vez. Nesse caso, utilizamos algumas diretivas que impedem que isso aconteça: 
- `#ifndef`: se não definido
  - Pule este código se já tiver sido incluído.
- `#define`
  - Define um nome para evitar dupla inclusão.
- `#endif`


    `sadsdasdasdsadasd`

```cpp
#ifndef TIME_H   // Include this block only if TIME_H is not defined
#define TIME_H   // On the first inclusion, define TIME_H to prevent
                 // this block from being included more than once.
// ..

#endif  // End of "#ifndef" 
````


## A Classe Time
Definiremos uma classe chamada Time que modela uma instância de tempo: hora, minuto e segundo.

- Três atributos (hora, minuto e segundo).
- Um construtor público que inicializa os atributos.
- Métodos "get" e "set" para gerenciar os atributos.
- Método público "print" para imprimir esta instância de tempo no formato hh:mm:ss.
- Um método público que adiciona um segundo.
```cpp
//Arquivo: time.h
class Time {
 private:  // Seção Privada
  // Membros privados
  int hour;     // 0 - 23
  int minute;   // 0 - 59
  int second;   // 0 - 59
 public:   // Seção Pública
  Time(int hour = 0, int minute = 0, int second = 0);         
  int getHour() const;   
  void setHour(int hour);   
  int getMinute() const; 
  void setMinute(int minute); 
  int getSecond() const; 
  void setSecond(int second);
  void print() const;
  void nextSecond();  
};  
````

No arquivo time.cpp, devemos incluir o arquivo time.h.
```cpp
/* Implementação da classe Time */
#include  <iostream>  // Para usar a função std::cout.
#include  "time.h"    // Para visualizar a classe Time.  

using  namespace  std; 	// Para escrever cout ao invés de		
						// std::cout.
````				
		
O próximo passo é incluir a implementação para todos os métodos. 
Para tanto, usamos o operador :: de resolução de escopo.
```cpp
int  Time::getHour() const {
	return hour;
}  
// ...
````
Com a Classe pronta , podemos utilizá-la em algum outro ponto do código.
```cpp
//Arquivo: time_main.cpp
  Time t1(23, 59, 59);   
  t1.print();       // 23:59:59
  t1.setHour(12);
  t1.setMinute(30);
  t1.setSecond(15);
  
  t1.print();       // 12:30:15
  cout << "Hour:    " << t1.getHour()   << endl;
  cout << "Minute:  " << t1.getMinute() << endl;
  cout << "Second:  " << t1.getSecond() << endl;
````
Para compilar o código completo, fazemos:

    $ g++ time_main.cpp time.cpp -o time

Feito isso, a execução será feita com:

    $ ./time
