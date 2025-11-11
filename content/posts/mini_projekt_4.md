---
date: 2025-11-04T18:35:02+02:00
# description: ""
featured_image: "/267859_ZPC_2025/images/el_fin.jpg"
lastmod: 2025-10-22
showTableOfContents: false
# tags: ["",]
title: "Mini projekt 5 - Binárne hodinky"
type: "post"
---
<!--more-->

Piaty projekt bol zameraný na elektroniku a Arduino. Rozhodol som sa vyrobiť binárne hodiny s teplomerom.

Elektrický obvod som navrhol tak, že som použil integrované obvody Tesla MH74193 (čítače), ktoré mi umožnili pripojiť viacero LED diód a jednoducho počítať čas. Tieto čítače totiž počítajú priamo v binárnom formáte, takže stačilo posielať impulzy každú minútu, resp. hodinu. Problém nastal pri rozsahu čítačov – jeden čítač dokáže počítať iba do 15 (4 bity), čo nestačí na 60 minút ani 24 hodín. Tento problém som vyriešil nasledovne:
-pri hodinovom čítači som pridal samostatnú LED diódu pripojenú na pin 5, ktorá signalizovala vyššie bity (nad 16),
-pri minútovom čítači som využil pin CA (Carry Out), ktorý vyšle impulz vždy, keď čítač prejde z 15 na 0. Tento signál som  pripojil na pin CU (Clock Up) druhého čítača, čím som dosiahol 8-bitové počítanie (pre minúty postačovalo 6 bitov).
<div style="display:flex; align-items:center; gap:8px;">
  <img src="/267859_ZPC_2025/images/el_schema.png" width="300"> 
  <img src="/267859_ZPC_2025/images/el_vrch.jpg" width="300">
</div>
Výsledné zapojenie teda umožnilo počítať až do 60 minút aj 24 hodín.Piny Q A–D boli pripojené na LED diódy, horný rad do počítača hodin a dolný minút, následne cez 220 Ω rezistory do zeme. Piny R (Reset) boli spojené a ovládané signálom z Arduina (Pin2), aby bolo možné jednotne vynulovať všetky čítače.
K Arduinu bolo pripojené aj tlačidlo – jeden pin bol pripojený na 5 V, druhý cez pulldown rezistor na zem a na vstup Arduina.Okrem toho bol pripojený aj teplomer, ktorého stredný pin bol pripojený na analógový vstup A0.
{{< myimg src="/267859_ZPC_2025/images/el_cel.jpg" width="500" alt="" >}}

Program na Arduine fungoval tak, že na začiatku poslal čítačom potrebný počet impulzov, aby LED diódy zobrazovali aktuálny čas.
Následne sa každú sekundu čas aktualizoval.
Ak bolo stlačené tlačidlo, Arduino vynulovalo čítače, prečítalo teplotu z analógového vstupu a vyslalo príslušný počet impulzov na minútové čítače, aby zobrazilo teplotu v binárnej forme.
<video src="/267859_ZPC_2025/images/el_vid.mp4" class="table-media" width="500" style="border-radius:20px; display:block;" autoplay loop muted playsinline></video>
<div style="max-height:400px; overflow-y:auto;">
<pre><code class="language-cpp">
const int clear_pin = 2;
const int clk_min_pin = 3;
const int clk_h_pin = 4;
const int led_pin = 5;
const int button_pin = 6;

int sek = 0;
int min = 53;
int h = 20;

int temp_val;
int temp;
bool cor_val = 1;

unsigned long prev_time = 0;

//funkcie zobrazenia casu
int set_min_leds(int num){
  for(int m = 0; m < num; m++){
    digitalWrite(clk_min_pin, LOW);
    delay(10);
    digitalWrite(clk_min_pin, HIGH);
  } 
}

int set_h_leds(int num){
  for(int h = 0; h < num; h++){
    digitalWrite(clk_h_pin, LOW);
    delay(10);
    digitalWrite(clk_h_pin, HIGH);
  }
  if(num>=16){
    digitalWrite(led_pin, HIGH);
  }
  else{
    digitalWrite(led_pin, LOW);
  }
}

//funkcie pridavania casu
int add_min(){
  digitalWrite(clk_min_pin, LOW);
  delay(10);
  digitalWrite(clk_min_pin, HIGH);
}

int add_h(){
  if(h>=16){
    digitalWrite(led_pin, HIGH);
  }
  else{
    digitalWrite(led_pin, HIGH);
  }
  digitalWrite(clk_h_pin, LOW);
  delay(10);
  digitalWrite(clk_h_pin, HIGH);
}

//funkcia resetu lediek
int res_leds(){
  digitalWrite(clear_pin, HIGH);
  delay(10);
  digitalWrite(clear_pin, LOW);
  digitalWrite(led_pin, LOW);
}

void setup() {
  pinMode(clk_min_pin, OUTPUT);
  digitalWrite(clk_min_pin, HIGH);
  pinMode(clk_h_pin, OUTPUT);
  digitalWrite(clk_h_pin, HIGH);

  pinMode(clear_pin, OUTPUT);

  pinMode(led_pin, OUTPUT);
  pinMode(button_pin, INPUT);

  //nahodenie pociatocneho casu
  res_leds();
  set_min_leds(min);
  set_h_leds(h);
}

void loop() {
  if((millis() - prev_time) >= 1000){
    prev_time = millis();
    sek++;

    //pridavanie casu
    if(sek >= 60){
      sek = 0;
      min++;
      add_min();
    }
    if(min >= 60){
      min = 0;
      h++;
      add_h();
    }
    if(h >= 24){
      h = 0;
      res_leds();
    }

    //ukazovanie teploty
    if (digitalRead(button_pin)&&cor_val) {
      res_leds();
      temp_val = analogRead(A0);
      temp = int((((temp_val / 1024.0) * 5.0 ) - 0.5) * 100.0);
      set_min_leds(temp);
      cor_val = 0;
    }
    if (!cor_val&&!digitalRead(button_pin)){
      res_leds();
      set_min_leds(min);
      set_h_leds(h);
      cor_val = 1;
    }

  }

}

</code></pre>
</div>
