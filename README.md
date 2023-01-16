# Sensor-Kebakaran
#Source code 
#include<SoftwareSerial.h>
SoftwareSerial module_bluetooth(0, 1);                  //komunikasi serial TX dan RX


int data = 0;                                           //variabel untuk bluetooth                                          //pin yang untuk relay
int spiker = A1;                                         //pin untuk buzzer
int sensorPin = A0;                                     //pin untuk sensor soil
int sensorValue = 0;                                    //variabel untuk sensor soil

void setup() {
  Serial.begin(9600);
  pinMode(spiker, OUTPUT);                              //mode pin buzzer sebagai output
}

void loop() {
  Serial.println("pembacaan sensor Api");      //menampilkan output text di monitor
  Serial.println(sensorValue);                        //menampilkan output text di monitor
  sensorValue = analogRead(sensorPin);                //memanggil variabel sensorValue sebagai sensor pin
  data = Serial.read();                               //meanggil variabel data

  if (sensorValue < 1000)                              //percabangan untuk sensor soil
  {
    Serial.println("Ada Api!!");                         //menampilkan output text di monitor
    digitalWrite(spiker, HIGH);                        //eksekusi untuk relay
    delay(1000);                                     //waktu untuk eksekusi
  }
  if (data == '1') {                                                      
    digitalWrite(spiker, HIGH);
    delay(1000);
  }
  else if (data == '0'){                             
    digitalWrite(spiker, LOW);                        
    delay(1000);
    }  
digitalWrite(spiker, LOW);
delay(1000);
}
