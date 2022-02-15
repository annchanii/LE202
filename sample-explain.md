## การทดลองที่1 การเขียนโปรแกรมเพื่อรันบนไมโครคอนโทรเลอร์
    #include <Arduino.h>   

    int cnt = 0;       --> * ประกาศตัวแปร cnt = 0 *

    void setup()      --> * ส่วน set up *

    {

	Serial.begin(115200);
    }

    void loop()         ---> *วนลูปทุกๆ 300 mSec*

    {

	cnt++;
	
	Serial.printf("A:%d\n",cnt);
	
	delay(300);
	
    }
## การทดลองที่ 2 เรื่อง การเขียนโปรแกรมค้นหาWiFi
    #include <Arduino.h>
    #include <ESP8266WiFi.h>       ---> *ใช้microcontroller ESP8266*

    int cnt = 0;                    --> *ประกาศตัวแปร cnt = 0*

    void setup()                --> *ส่วน set up WiFi*
    {
	Serial.begin(115200);
	WiFi.mode(WIFI_STA);
	WiFi.disconnect();
	delay(100);                  ----> *delay ทุกๆ 100 mSec*
	Serial.println("\n\n\n");
     }

    void loop()                      ---> *วนลูปทุกๆ 10 mSec*
    {
	Serial.println("========== เริ่มต้นแสกนหา Wifi ===========");    ---> *แสดงข้อความค้นหาWiFi*
	int n = WiFi.scanNetworks();
	if(n == 0) {                                      ---> *ถ้า n=0 แสดง no network found*
		Serial.println("NO NETWORK FOUND");
	} else {
		for(int i=0; i<n; i++) {
			Serial.print(i + 1);
			Serial.print(": ");
			Serial.print(WiFi.SSID(i));
			Serial.print(" (");
			Serial.print(WiFi.RSSI(i));
			Serial.print(")");
			Serial.println((WiFi.encryptionType(i) == ENC_TYPE_NONE)?" ":"*");
			delay(10);
		}
	}
	Serial.println("\n\n");
    }
 ## การทดลองที่ 3 เรื่อง การเขียนโปรแกรมเอาท์พุทสัญญาณดิจิทัล
    
    #include <Arduino.h>
    #include <ESP8266WiFi.h>     ---> *ใช้microcontroller ESP8266*

    int cnt = 0;                 --> *ประกาศตัวแปร cnt = 0*

    void setup()                 --> *ส่วน set up*
     {
	Serial.begin(115200);
	pinMode(0, OUTPUT);        ---> *ให้ 0 เป็น output*
	Serial.println("\n\n\n");
     }

    void loop()           ---> *วนลูปทุกๆ 500 mSec*
    {
	cnt++;
	if(cnt % 2) {
		Serial.println("========== ON ===========");
		digitalWrite(0, HIGH);
	} else {
		Serial.println("========== OFF ===========");
		digitalWrite(0, LOW);
	}
	delay(500);
    }
