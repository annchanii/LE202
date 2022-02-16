## การทดลองที่1 การเขียนโปรแกรมเพื่อรันบนไมโครคอนโทรเลอร์
     #include <Arduino.h>   

    int cnt = 0;                       --> ประกาศตัวแปร cnt = 0 

    void setup()                    --> ส่วน set up 

    {

	Serial.begin(115200);
    }

    void loop()         ---> วนลูปทุกๆ 300 mSec

    {

	cnt++;
	
	Serial.printf("A:%d\n",cnt);         ---แสดงค่าตัวแปร cnt
	
	delay(300);
	
    }
## การทดลองที่ 2 เรื่อง การเขียนโปรแกรมค้นหาWiFi
    #include <Arduino.h>
    #include <ESP8266WiFi.h>       ---> ใช้microcontroller ESP8266

    int cnt = 0;                    --> ประกาศตัวแปร cnt = 0

    void setup()                --> ส่วน set up WiFi
    {
	Serial.begin(115200);
	WiFi.mode(WIFI_STA);
	WiFi.disconnect();
	delay(100);                  ----> delay ทุกๆ 100 mSec
	Serial.println("\n\n\n");
     }

    void loop()                      ---> วนลูปทุกๆ 10 mSec
    {
	Serial.println("========== เริ่มต้นแสกนหา Wifi ===========");    ---> แสดงข้อความค้นหาWiFi
	int n = WiFi.scanNetworks();                                  ---> แสดงจำนวนเครือข่ายที่พบในรูป n
	if(n == 0) {                                      ---> ถ้า n=0 แสดง no network found
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
    #include <ESP8266WiFi.h>     ---> ใช้microcontroller ESP8266

    int cnt = 0;                 --> ประกาศตัวแปร cnt = 0

    void setup()                 --> ส่วน set up
     {
	Serial.begin(115200);
	pinMode(0, OUTPUT);        ---> ให้ 0 เป็น output
	Serial.println("\n\n\n");
     }

    void loop()           ---> วนลูปทุกๆ 500 mSec
    {
	cnt++;
	if(cnt % 2) {                                          ----> ถ้า cnt = เลขคู่ ให้แสดง on
		Serial.println("========== ON ===========");
		digitalWrite(0, HIGH);                        ----> ให้ส่ง High ไปที่พอร์ท 0 
	} else {                                              ----> ถ้า cnt = เลขคี่ ให้แสดง off
		Serial.println("========== OFF ===========");
		digitalWrite(0, LOW);                          ----> ให้ส่ง Low ไปที่พอร์ท 0 
	}
	delay(500);
    }
    
 ## การทดลองที่ 4 เรื่อง การเขียนโปรแกรมอินพุทสัญญาณดิจิทัล
    #include <Arduino.h>
    #include <ESP8266WiFi.h>       ---> ใช้microcontroller ESP8266

    int cnt = 0;                      --> ประกาศตัวแปร cnt = 0

    void setup()                     --> ส่วน set up
    {
	Serial.begin(115200);
	pinMode(0, INPUT);               ---> กำหนดให้ 0 เป็น input
	pinMode(2, OUTPUT);               ---> กำหนดให้ 2 เป็น output
	Serial.println("\n\n\n");
    }

    void loop()                            ---> วนลูปทุกๆ 100 mSec
    {
	int val = digitalRead(0);               ---> ให้อ่านข้อมูลจากพอร์ท 0
	Serial.printf("======= read %d\n", val);
	if(val==1) {                            ---> ถ้า val = 1
		digitalWrite(2, LOW);           ---> ส่ง low ไปที่พอร์ท 2
	} else {                               ----> ถ้า val ไม่เทมากับ 1
		digitalWrite(2, HIGH);         ---> ส่ง low ไปที่พอร์ท 2
	}
	delay(100);
    }


## การทดลองที่ 5 เรื่อง การเขียนโปรแกรมเชื่อมต่อไวไฟและเว็บเซอร์เวอร์
    #include <ESP8266WiFi.h>
    //#include <WiFiClient.h>
    #include <ESP8266WebServer.h>               ---> ใช้microcontroller ESP8266

    const char* ssid = "HI_BMFWIFI_2.4G";       ---> ใส่ชื่อWiFi
    const char* password = "0819110933";         ---> ใส่ password WiFi

    ESP8266WebServer server(80);

    int cnt = 0;             --> ประกาศตัวแปร cnt = 0

     void setup(void){              --> ส่วน set up ให้เชื่อมกับ WiFi
	Serial.begin(115200);                  ----> set เริ่มที่ความเร็ว 115200 B/s

	WiFi.mode(WIFI_STA);
	WiFi.begin(ssid, password);
	while (WiFi.status() != WL_CONNECTED) {        ---> เชื่อมกับWiFiที่เราใส่ชื่อไว้
		delay(500);
		Serial.print(".");
	}
	Serial.print("\n\nIP address: ");
	Serial.println(WiFi.localIP());

	server.onNotFound([]() {
		server.send(404, "text/plain", "Path Not Found");     ---> ถ้าหาไม่เจอจะแสดง not found
	});

	server.on("/", []() {
		cnt++;
		String msg = "Hello cnt: ";          ---> ถ้ามีการเชื่อม ให้แสดง Hello cnt
		msg += cnt;
		server.send(200, "text/plain", msg);
	});

	server.begin();
	Serial.println("HTTP server started");
    }

    void loop(void){
    server.handleClient();
    }
    
 ## การทดลองที่ 6 เรื่อง การเขียนโปรแกรมสร้างไวไฟแอคเซสพอยต์ (Wifi AP)
    #include <ESP8266WiFi.h>               ---> ใช้microcontroller ESP8266
    //#include <WiFiClient.h>
    #include <ESP8266WebServer.h>

    const char* ssid = "MY-ESP8266";           ---> กำหนดชื่อWiFi
    const char* password = "choompol";        ---> กำหนด password WiFi

    IPAddress local_ip(192, 168, 1, 1);     ---> ใส่ IP address local_ip
    IPAddress gateway(192, 168, 1, 1);       ---> ใส่ IP address gateway
    IPAddress subnet(255, 255, 255, 0);      ---> ใส่ IP address subnet

    ESP8266WebServer server(80);

    int cnt = 0;                           --> ประกาศตัวแปร cnt = 0

    void setup(void){                      --> ส่วน set up ให้เชื่อมกับ WiFi
	Serial.begin(115200);              ----> set เริ่มที่ความเร็ว 115200 B/s

	WiFi.softAP(ssid, password);          
	WiFi.softAPConfig(local_ip, gateway, subnet);
	delay(100);

	server.onNotFound([]() {                         --> ถ้าหาไม่เจอจะแสดง not found
		server.send(404, "text/plain", "Path Not Found");
	});

	server.on("/", []() {
		cnt++;
		String msg = "Hello cnt: ";               ---> ถ้ามีการเชื่อม ให้แสดง Hello cnt
		msg += cnt;
		server.send(200, "text/plain", msg);
	});

	server.begin();
	Serial.println("HTTP server started");
    }

    void loop(void){
      server.handleClient();
    }
