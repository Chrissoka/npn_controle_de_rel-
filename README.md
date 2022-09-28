# lampada-npn_no_controle_de_rele
**Projeto circuito de lâmpada com controle rele-npn**

# IMAGEM DO CIRCUITO
![projeto_controle_npn_botao](https://user-images.githubusercontent.com/90460886/192660947-156f0673-1487-4219-8533-a7d3a9207e80.png)

# CÓDIGO
*C++*


    
    int pinButton = 8;
    int Relay = 2;
    int stateRelay = LOW;
    int stateButton;
    int previous = LOW;
    long time = 0;
    long debounce = 100;


    int stayON = 5000;

    void setup() {
      pinMode(pinButton, INPUT);
      pinMode(Relay, OUTPUT);
    }

    void loop() {
      stateButton = digitalRead(pinButton);  
      if(stateButton == HIGH && previous == LOW && millis() - time > debounce) {
        if(stateRelay == HIGH){
          digitalWrite(Relay, LOW);
        } else {


           digitalWrite(Relay, HIGH);
           delay(stayON);
           digitalWrite(Relay, LOW);
        }
        time = millis();
      }
      previous == stateButton;
    }


