<h1>Data e Hora no Java</h1>



Java disponibiliza algumas opções para trabalhar com data e hora, mas nenhuma delas é tão robusta quanto a API java.time, que foi introduzida na versão 8 da Linguagem Java. Esta nova API foi criada com o objetivo de resolver problemas que tínhamos com as Classes **Date e Calendar**, graças aos seus Métodos, que simplificam e muito o processamento de datas e horários.

<h2>1. Principais Classes da API java.time</h2>

A API java.time, oferece 3 Classes para trabalhar com data e hora:

| Classe            | Descrição                |
| ----------------- | ------------------------ |
| **LocalDate**     | Armazena apenas a data   |
| **LocalTime**     | Armazena apenas a hora   |
| **LocalDateTime** | Armazena a data e a hora |

Existem 3 Métodos principais para criar um novo Objeto das Classes LocalDate, LocalTime e LocalDateTime, como mostra a tabela abaixo:

| Métodos     | Descrição                                                    |
| :---------- | :----------------------------------------------------------- |
| **now()**   | Método utilizado para retornar a instância das Classes LocalDate, LocalTime ou LocalDateTime, com a Data e/ou Hora atual do sistema. |
| **of()**    | Método utilizado para retornar a instância das Classes LocalDate, LocalTime ou LocalDateTime com valores específicos. |
| **parse()** | Método utilizado para converter uma String em uma instância das Classes LocalDate, LocalTime ou LocalDateTime. |

<br />

No exemplo abaixo, vemos como instanciar os Objetos das Classes LocalDate, LocalTime e LocalDateTime, e na sequência visualizar na tela:

<img src="https://i.imgur.com/gsSDe7P.png" title="source: imgur.com" width="3%"/>**Exemplo 01 - Instanciando e Visualizando Objetos da API java.time:** 

```java
package data_hora;

import java.time.LocalDate;
import java.time.LocalDateTime;
import java.time.LocalTime;

public class DataHora {

	public static void main(String[] args) {

		// Objeto LocalDate com a data atual
		LocalDate data = LocalDate.of(2019, 11, 25);

		// Objeto LocalDate com a data e hora atual
		LocalDateTime dataHora = LocalDateTime.now();

		// Objeto LocalDate com a hora atual
		LocalTime hora = LocalTime.parse("19:34:50");
		
		//Exibir os Objetos na tela
		System.out.println("\nData atual: " + data);
		System.out.println("\nData e Hora atual: " + dataHora);
		System.out.println("\nHora atual: " + hora);

	}

}
```

Através do Método **now()**, as Classes da API java.time consultam a data e a hora do sistema e gera um novo Objeto armazenando estas informações. Ao executar o código, será exibido no console o seguinte resultado:

<img src="https://i.imgur.com/V2ReOnx.png" title="source: imgur.com" width="3%"/>**Resultado do Algoritmo:**

```bash
Data atual: 2019-11-25

Data e Hora atual: 2022-11-26T08:44:14.583707800

Hora atual: 19:34:50
```

<br />

<div align="left"><img src="https://i.imgur.com/JSfXyzm.png" title="source: imgur.com" width="30px"/> <a href="https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/time/LocalDate.html" target="_blank"><b>Documentação: Classe LocalDate</b></a>

<div align="left"><img src="https://i.imgur.com/JSfXyzm.png" title="source: imgur.com" width="30px"/> <a href="https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/time/LocalDateTime.html" target="_blank"><b>Documentação: Classe LocalDateTime</b></a>

<div align="left"><img src="https://i.imgur.com/JSfXyzm.png" title="source: imgur.com" width="30px"/> <a href="https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/time/LocalTime.html" target="_blank"><b>Documentação: Classe LocalTime</b></a>

<br /><br />

<div align="left"><img src="https://i.imgur.com/JACNZiR.png" title="source: imgur.com" width="25px"/> <a href="https://github.com/rafaelq80/exemplos_java/tree/main/data_hora/data_hora_v1" target="_blank"><b>Código fonte: Exemplo 01</b></a>

<br />

<h2>2. Formatando a Data e a Hora</h2>

Observe no Exemplo 01, que a data e a hora foram exibidas no padrão americano. Através da Classe **DateTimeFormatter** é possível formatar a saída no console. 

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="200px"/> | <div align="left"> **ALERTA DE BSM:** *Mantenha a Atenção aos Detalhes ao trabalhar com a Classe DateTimeFormatter. A Classe DateTimeFormatter formata apenas a exibição na tela, ou seja, no Objeto ou no Banco de dados o formato americano será mantido.* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<h3>2.1. Padrões de Formatação</h3>

Para formatar a data e hora, a Classe DateTimeFormatter utiliza alguns códigos de formatação, chamados **patterns** (padrões), que em conjunto criam o padrão desejado. Na tabela abaixo, temos a lista de códigos:

| Símbolo | Descrição              | Formato |
| ------- | ---------------------- | ------- |
| y       | ano                    | Número  |
| D       | dia do ano             | Número  |
| M       | mês do ano             | Número  |
| L       | mês do ano por extenso | Texto   |
| Y       | ano                    | Número  |
| E       | dia da semana          | Texto   |
| a       | AM PM                  | Texto   |
| h       | hora (1-12)            | Número  |
| k       | hora (1-24)            | Número  |
| m       | minutos                | Número  |
| s       | segundos               | Número  |
| n       | milisegundos           | Número  |

Veja a aplicação de alguns padrões de formatação comuns no exemplo abaixo:

<img src="https://i.imgur.com/gsSDe7P.png" title="source: imgur.com" width="3%"/>**Exemplo 02 - Formatação de Data e Hora:** 

```java
package data_hora;

import java.time.LocalDate;
import java.time.LocalDateTime;
import java.time.LocalTime;
import java.time.format.DateTimeFormatter;

public class DataHora {

	public static void main(String[] args) {

		// Objeto LocalDate com a data atual
		LocalDate data = LocalDate.now();
		LocalDateTime dataHora = LocalDateTime.now();
		LocalTime hora = LocalTime.now();
		
		//Exibir na tela o Objeto da Classe LocalDate formatado
		System.out.println("Data no formato do Brasil: " + 
                          data.format(DateTimeFormatter.ofPattern("dd/MM/yyyy")));
		System.out.println("\nData com o mês por extenso: " + 
                          data.format(DateTimeFormatter.ofPattern("dd/MMMM/YYYY")));
		System.out.println("\nData com o dia da semana: " + 
                          data.format(DateTimeFormatter.ofPattern("EEEE, dd/MM/yyyy")));
		
		//Exibir na tela o Objeto da Classe LocalTime formatado
		System.out.println("\nHora no formato do Brasil: " + 
                          hora.format(DateTimeFormatter.ofPattern("hh:mm:ss")));
		System.out.println("\nHora com milisegundos: " + 
                          hora.format(DateTimeFormatter.ofPattern("hh:mm:ss.n")));
		System.out.println("\nHora no formato AM/PM: " + 
                          hora.format(DateTimeFormatter.ofPattern("kk:mm:ss a")));

		//Exibir na tela o Objeto da Classe LocalDateTime formatado
		System.out.println("\nData e Hora no formato do Brasil: " + 
                          dataHora.format(DateTimeFormatter.ofPattern("dd/MM/yyyy hh:mm:ss")));
				
	}

}

```

Através do Método **format()**, da API java.time, aplicamos a formatação deseja e através do Método **ofPattern()**, da Classe **DateTimeFormatter**, definimos o padrão de formatação desejado. Ao executar o código, será exibido no console o seguinte resultado:

<img src="https://i.imgur.com/V2ReOnx.png" title="source: imgur.com" width="3%"/>**Resultado do Algoritmo:**

```bash
Data no formato do Brasil: 26/11/2022

Data com o mês por extenso: 26/novembro/2022

Data com o dia da semana: sábado, 26/11/2022

Hora no formato do Brasil: 08:26:36

Hora com milisegundos: 08:26:36.191367400

Hora no formato AM/PM: 08:26:36 AM

Data e Hora no formato do Brasil: 26/11/2022 08:26:36
```

<br />

<div align="left"><img src="https://i.imgur.com/JSfXyzm.png" title="source: imgur.com" width="30px"/> <a href="https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/time/format/DateTimeFormatter.html" target="_blank"><b>Documentação: Classe DateTimeFormatter</b></a>

<br /><br />

<div align="left"><img src="https://i.imgur.com/JACNZiR.png" title="source: imgur.com" width="25px"/> <a href="https://github.com/rafaelq80/exemplos_java/tree/main/data_hora/data_hora_v2" target="_blank"><b>Código fonte: Exemplo 02</b></a>

<br />

<h2>3. Principais Métodos da Classe LocalDate</h2>

| Métodos                       | Descrição                                                    |
| :---------------------------- | :----------------------------------------------------------- |
| **compareTo(LocalDate data)** | Este método verifica se esta data é igual a outra data. Se forem iguais, será retornado 0, caso seja menor ou maior, será retornada a diferença em anos a mais (numero inteiro positivo) ou a menos (numero inteiro negativo). |
| **equals(LocalDate data)**    | Este método verifica se esta data é igual a outra data. Se forem iguais, será retornado true, caso contrário será retornado false. |
| **getDayOfMonth()**           | Este método obtém o campo dia do mês.                        |
| **getDayOfYear()**            | Este método obtém o campo dia do ano.                        |
| **getYear()**                 | Este método obtém o campo ano de uma data.                   |
| **getMonthValue()**           | Este método obtém o campo mês de 1 a 12.                     |
| **isAfter(LocalDate data)**   | Este método verifica se esta data é posterior à data especificada. |
| **isBefore(LocalDate data)**  | Este método verifica se esta data é anterior à data especificada. |
| **isEqual(LocalDate data)**   | Este método verifica se esta data é igual à data especificada. |
| **isLeapYear()**              | Este método verifica se o ano é bissexto.                    |

No exemplo abaixo, veremos o uso dos Métodos da Classe LocalDate:

<img src="https://i.imgur.com/gsSDe7P.png" title="source: imgur.com" width="3%"/>**Exemplo 03 - Métodos da Classe LocalDate:** 


```java
package data_hora;

import java.time.LocalDate;

public class DataHora {

	public static void main(String[] args) {

		// Instanciar uma novo objeto LocalDate
		LocalDate data = LocalDate.now();

		// Obter detalhes sobre a data
		System.out.println("\nExibir apenas o Dia da data: " + data.getDayOfMonth());
		System.out.println("\nExibir apenas o numero do dia do ano da data: " + data.getDayOfYear());
		System.out.println("\nExibir apenas o mês da data: " + data.getMonthValue());
		System.out.println("\n" + data.getYear() + " é um ano Bissexto? " + data.isLeapYear());
		System.out.println("\nQuantos dias tem o mês " + data.getMonthValue() + "? " + data.lengthOfMonth());
		System.out.println("\nQuantos dias tem o ano " + data.getYear() + "? " + data.lengthOfYear());

		/**
		 * Instanciar 3 Objetos da Classe LocalDate, que serão utilizados nos Métodos de
		 * comparação entre datas
		 */
		LocalDate dataMenor = LocalDate.of(2019, 11, 25);
		LocalDate dataIgual = LocalDate.now();
		LocalDate dataMaior = LocalDate.of(2025, 11, 25);

		// Comparação entre datas
		System.out.println("\nA data: " + dataMenor + " é igual a data: " + data + "? " + data.equals(dataMenor));
		System.out.println("\nA data: " + dataIgual + " é igual a data: " + data + "? " + data.equals(dataIgual));
		System.out.println("\nA data: " + dataMaior + " é igual a data: " + data + "? " + data.equals(dataMaior));

		System.out.println("\nA data: " + data + " é maior do que a data: " + dataMenor + " aproximadamente " + data.compareTo(dataMenor) + " anos");
		System.out.println("\nA data: " + data + " é menor do que a data: " + dataMaior + " aproximadamente " + data.compareTo(dataMaior) + " anos");

		System.out.println("\nA data: " + data + " é posterior a data: " + dataMenor + "? " + data.isAfter(dataMenor));
		System.out.println("\nA data: " + data + " é igual a data: " + dataIgual + "? " + data.isEqual(dataIgual));
		System.out.println("\nA data: " + data + " é anterior a data: " + dataMaior + "? " + data.isBefore(dataMaior));

	}

}

```

<img src="https://i.imgur.com/V2ReOnx.png" title="source: imgur.com" width="3%"/>**Resultado do Algoritmo:**

```bash

Exibir apenas o Dia da data: 26

Exibir apenas o numero do dia do ano da data: 330

Exibir apenas o mês da data: 11

2022 é um ano Bissexto? false

Quantos dias tem o mês 11? 30

Quantos dias tem o ano 2022? 365

A data: 2019-11-25 é igual a data: 2022-11-26? false

A data: 2022-11-26 é igual a data: 2022-11-26? true

A data: 2025-11-25 é igual a data: 2022-11-26? false

A data: 2022-11-26 é maior do que a data: 2019-11-25, aproximadamente 3 anos

A data: 2022-11-26 é menor do que a data: 2025-11-25, aproximadamente -3 anos

A data: 2022-11-26 é posterior a data: 2019-11-25? true

A data: 2022-11-26 é igual a data: 2022-11-26? true

A data: 2022-11-26 é anterior a data: 2025-11-25? true
```

<br />

<div align="left"><img src="https://i.imgur.com/JACNZiR.png" title="source: imgur.com" width="25px"/> <a href="https://github.com/rafaelq80/exemplos_java/tree/main/data_hora/data_hora_ld" target="_blank"><b>Código fonte: Exemplo 03</b></a>


<br />

<h2>4. Principais Métodos da Classe LocalTime</h2>

| Método                        | Descrição                                                    |
| :---------------------------- | :----------------------------------------------------------- |
| **compareTo(LocalTime hora)** | Este método compara dois horários. Se forem iguais, será retornado 0, se for maior será retornado 1 e se for menor será retornado -1. |
| **equals(LocalTime hora)**    | Este método verifica se um horário é igual a outro horário. Se forem iguais, será retornado true, caso contrário será retornado false. |
| **getHour()**                 | Este método obtém o campo hora do dia.                       |
| **getMinute()**               | Este método obtém o campo minuto da hora.                    |
| **getNano()**                 | Este método obtém o campo milisegundo.                       |
| **getSecond()**               | Este método obtém o campo do segundo do minuto.              |
| **isAfter(LocalTime hora)**   | Este método verifica se este horário é posterior ao horário especificado. |
| **isBefore(LocalTime hora)**  | Este método verifica se esta hora é anterior à hora especificada. |

No exemplo abaixo, veremos alguns usos dos Métodos da Classe LocalTime:

<img src="https://i.imgur.com/gsSDe7P.png" title="source: imgur.com" width="3%"/>**Exemplo 04 - Métodos da Classe LocalDate:** 


```java
package data_hora;

import java.time.LocalTime;

public class DataHora {

	public static void main(String[] args) {

		// Instanciar uma novo objeto LocalTime
		LocalTime hora = LocalTime.now();

		// Obter detalhes sobre a hora
		System.out.println("\nExibir apenas a hora: " + hora.getHour());
		System.out.println("\nExibir apenas os minutos: " + hora.getMinute());
		System.out.println("\nExibir apenas os segundos: " + hora.getSecond());
		System.out.println("\nExibir os Milisegundos: " + hora.getNano());

		/**
		 * Instanciar 3 Objetos da Classe LocalTime, que serão utilizados nos Métodos de
		 * comparação entre horas
		 */
		LocalTime horaMenor = LocalTime.of(8, 30, 25);
		LocalTime horaIgual = LocalTime.now();
		LocalTime horaMaior = LocalTime.of(10, 30, 25);

		// Comparação entre horas
		System.out.println("\nA hora: " + horaMenor + " é igual a hora: " + hora + "? " + 
                           hora.equals(horaMenor));
		System.out.println("\nA hora: " + horaIgual + " é igual a hora: " + hora + "? " + 
                           hora.equals(horaIgual));
		System.out.println("\nA hora: " + horaMaior + " é igual a hora: " + hora + "? " + 
                           hora.equals(horaMaior));

		System.out.println("\nA hora: " + hora + " é maior do que a hora: " + 
                           horaMenor + " (" + hora.compareTo(horaMenor) + ")");
		System.out.println("\nA hora: " + hora + " é menor do que a hora: " + 
                           horaMaior + " (" + hora.compareTo(horaMaior) + ")");

		System.out.println("\nA hora: " + hora + " é posterior a hora: " + horaMenor + "? " + 
                           hora.isAfter(horaMenor));
		System.out.println("\nA hora: " + hora + " é anterior a hora: " + horaMaior + "? " + 
                           hora.isBefore(horaMaior));

	}

}
```

<img src="https://i.imgur.com/V2ReOnx.png" title="source: imgur.com" width="3%"/>**Resultado do Algoritmo:**

```bash

Exibir apenas a hora: 9

Exibir apenas os minutos: 41

Exibir apenas os segundos: 8

Exibir os Milisegundos: 782424500

A hora: 08:30:25 é igual a hora: 09:41:08.782424500? false

A hora: 09:41:08.783427800 é igual a hora: 09:41:08.782424500? false

A hora: 10:30:25 é igual a hora: 09:41:08.782424500? false

A hora: 09:41:08.782424500 é maior do que a hora: 08:30:25 (1)

A hora: 09:41:08.782424500 é menor do que a hora: 10:30:25 (-1)

A hora: 09:41:08.782424500 é posterior a hora: 08:30:25? true

A hora: 09:41:08.782424500 é anterior a hora: 10:30:25? true
```

<br />

<div align="left"><img src="https://i.imgur.com/JACNZiR.png" title="source: imgur.com" width="25px"/> <a href="https://github.com/rafaelq80/exemplos_java/tree/main/data_hora/data_hora_lt" target="_blank"><b>Código fonte: Exemplo 04</b></a>


<br />

<h2>5. Classes Period e Duration</h2>

A classe **Period** representa uma quantidade de tempo em termos de anos, meses e dias. A classe Period é muito utilizada para modificar valores de uma determinada data ou para obter a diferença entre duas datas.

A classe **Duration** representa uma quantidade de tempo em termos de segundos e milissegundos. A classe Duration é muito utilizada para modificar valores de uma determinada hora ou para obter a diferença entre duas horas.

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="100px"/> | <div align="left"> **ALERTA DE BSM:** *Mantenha a Atenção aos Detalhes ao trabalhar com as Classes Period e Duration. As Classes Classes Period e Duration não aceitam Objetos da Classe LocalDateTime.* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

No exemplo abaixo, veremos como utilizar as Classes Period e Duration, para encontrar a diferença entre duas datas em anos e dois horários em segundos:

<img src="https://i.imgur.com/gsSDe7P.png" title="source: imgur.com" width="3%"/>**Exemplo 05 - Classe Period e Duration** 


```java
package data_hora;

import java.time.Duration;
import java.time.LocalDate;
import java.time.LocalTime;
import java.time.Period;

public class DataHora {

	public static void main(String[] args) {

		// Objeto LocalDate com uma data específica
		LocalDate data = LocalDate.of(2019, 11, 25);

		// Objeto LocalDate com uma hora específica
		LocalTime hora = LocalTime.of(6, 30, 0);
		
		// Comparar uma data específica com a data de hoje
		System.out.println("\nDiferença em anos: " + Period.between(data, LocalDate.now()).getYears());
		
		// Comparar uma hora específica com a hora atual
		System.out.println("\nDiferença em segundos: " + Duration.between(hora, LocalTime.now()).getSeconds());

	}

}
```

<img src="https://i.imgur.com/V2ReOnx.png" title="source: imgur.com" width="3%"/>**Resultado do Algoritmo:**

```bash
Diferença em anos: 3

Diferença em segundos: 13143
```

<br />

<div align="left"><img src="https://i.imgur.com/JSfXyzm.png" title="source: imgur.com" width="30px"/> <a href="https://docs.oracle.com/javase/8/docs/api/java/time/Period.html" target="_blank"><b>Documentação: Classe Period</b></a>

<div align="left"><img src="https://i.imgur.com/JSfXyzm.png" title="source: imgur.com" width="30px"/> <a href="https://docs.oracle.com/javase/8/docs/api/java/time/Duration.html" target="_blank"><b>Documentação: Classe Duration</b></a>

<br /><br />

<div align="left"><img src="https://i.imgur.com/JACNZiR.png" title="source: imgur.com" width="25px"/> <a href="https://github.com/rafaelq80/exemplos_java/tree/main/data_hora/data_hora_period" target="_blank"><b>Código fonte: Exemplo 05</b></a>

<br />
<br />

<div align="left"><a href="README.md"><img src="https://i.imgur.com/XMgF3gl.png" title="source: imgur.com" width="3%"/>Voltar</a></div>