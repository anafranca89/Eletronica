# Semáforo com simulação de trânsito

## Descrição
O projeto simula um semáforo e um carro que será controlado pelo usuário por um botão. Se o usuário tentar passar no sinal vermelho e amarelo, um alarme soará.
O projeto foi simulado digitalmente no site Tinkercad.

![Imagem do circuito projetado no Tinkercad](img/imgcircuito.jpg)

[Link para o circuito no Tinkercad](https://www.tinkercad.com/things/cAcLReR0zg6-semaforo-com-o-aviso-de-passou-no-farol-vermelho?sharecode=51FGQJrBNMYSjFHFrg-ELpj4igLAnCl1bAkZp8bi810)

## Componentes Utilizados:

| Quant. | Nome do Componente | Especificação | Valor |
|---|---|---|---|
| 1| Protoboard| 400 pontos   | R$ 21,70 |
| 3| LED difuso |  5mm     | R$ 1,50 | 
| 1| Buzzer |      |  |
| 1| Push button|     | R$ 1,00 | 
| 3 | Resistores|   | R$ 0,70 - 10 unidades | 
| TOTAL |--------- |--------- |R$ 24,90|


## Explicação do uso dos componentes: 

### LEDs 
Com cores vermelho, amarelo e verde, são utilizados para representar o funcionamento de um semáforo. Suportam uma corrente máxima de 20mA.

### Resistores
Utilizados para controlar a corrente que passa pelo LED. A tensão utilizada no circuito é 5V do arduino. Os LEDs suportam até  20mA(0,02A) de corrente sem queimar. Logo, utilizando a 1° Lei de Ohm:
> V = R * I \
> 5V = R * 20mA
> R = 250 Ω \
Devemos ter no mínimo 250Ω nos resistores, então os resistores de 330Ω funcionam bem para o circuito. 


### Push Button:
É o componente interativo do sistema, que ira representar o trânsito de um carro quando estiver pressionado.

### Buzzer:
É o componente utilizado para soar o alarme.

## Código Arduino;
````c++
int counter;

void setup()
{
  pinMode(13, OUTPUT);
  pinMode(11, OUTPUT);
  pinMode(8, INPUT);
  pinMode(5, OUTPUT);
  pinMode(12, OUTPUT);

  for (counter = 0; counter < 1000; ++counter) {
    digitalWrite(11, HIGH);
    digitalWrite(13, LOW);
    delay(1500); // Wait for 1500 ms

    digitalWrite(11, LOW);
    digitalWrite(12, HIGH);

    if (digitalRead(8) == HIGH) {
      tone(5, 1000, 1500); // Play 700 Hz tone for 1500 ms
    }
    delay(1500);

    digitalWrite(12, LOW);
    digitalWrite(13, HIGH);

    if (digitalRead(8) == HIGH) {
      tone(5, 500, 1500); // Play 1000 Hz tone for 1500 ms
    }
    delay(1500);

    noTone(5);  // Stop any tone on pin 5
  }
}

void loop()
{
  delay(10); // Small delay for performance
}

`````
## Imagens do Projeto:

![Imagem do projeto físico]()

![Imagem do projeto físico]()

![Imagem do circuito projetado no Tinkercad](img/imgcircuito.jpg)

