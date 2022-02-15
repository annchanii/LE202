## การทดลองที่1 การเขียนโปรแกรมเพื่อรันบนไมโครคอนโทรเลอร์
#include <Arduino.h>  

int cnt = 0;       --> *ประกาศตัวแปร cnt = 0*

void setup()      --> *ส่วน set up*

{
	Serial.begin(115200);
}


void loop()         ---> *วนลูปทุกๆ 300 mSec*

{
	cnt++;
	Serial.printf("A:%d\n",cnt);
	delay(300);
}

