# Anti-Accident-Junction-Spike-system-AAJS-
The project titled ‘Anti Accident  Junction Spike system (AAJS)’ focuses on the road safety. This is an innovative idea to stop the violation of the traffic signals and thereby reduce the number of road accidents. We included a spike system along with the normal signal system. And also we have provided a RF module to control the spikes and traffic lights. When the traffic signal become yellow  spikes will rise and  this lasts till the signal again become yellow ,so it is not possible for the vehicles to cross the road when the signal is red . When the time arrives, the signal turn back to yellow, from that moment itself spike system will move down. When the signal becomes green the spike will be down completely from the road so that vehicles can pass. The working of the alternate road is similar but opposite.  When the first signal turns red   then alternate signal turns green. That is when the first signal becomes yellow, the first spike goes up and the alternate spike turns down. In case of some emergency situations like fire engine and ambulances to pass through, the spike system can be externally controlled by the RF module. The spike can be forcefully made down using keys in the RF module so that the vehicle can pass. This system also ensures smooth and fast riding of these emergency vehicles by turning on red lights. The main objective of this project named ‘Anti Accident  Junction Spike system (AAJS)’ is ensuring road safety  and it also tempts people to obey traffic rules and come under  the pillar  law enforcement .  We hope this project will be a new mile stone in the field of electronics and law enforcement in road safety at junctions.

program code

sbit DTMF1 at RC0_bit;
sbit DTMF2 at RC1_bit;
sbit DTMF3 at RC2_bit;
sbit DTMF4 at RC3_bit;

sbit Red1 at RB0_bit;
sbit Yellow1 at RB1_bit;
sbit Green1 at RB2_bit;

sbit Red2 at RB3_bit;
sbit Yellow2 at RB4_bit;
sbit Green2 at RB5_bit;


 void servoRotate0_2() 
{
  unsigned int i;
  for(i=0;i<50;i++)
  {
    PORTB.F6 = 1;
    Delay_us(800);
    PORTB.F6 = 0;
    Delay_us(19200);
  }
}

void servoRotate90_2() 
{
  unsigned int i;
  for(i=0;i<50;i++)
  {
    PORTB.F6 = 1;
    Delay_us(1500);
    PORTB.F6 = 0;
    Delay_us(18500);
  }
}
void servoRotate0() 
{
  unsigned int i;
  for(i=0;i<50;i++)
  {
    PORTB.F7 = 1;
    Delay_us(800);
    PORTB.F7 = 0;
    Delay_us(19200);
  }
}

void servoRotate90() 
{
  unsigned int i;
  for(i=0;i<50;i++)
  {
    PORTB.F7 = 1;
    Delay_us(1500);
    PORTB.F7 = 0;
    Delay_us(18500);
  }
}

void servoRotate180() 
{
  unsigned int i;
  for(i=0;i<50;i++)
  {
    PORTB.F0 = 1;
    Delay_us(2200);
    PORTB.F0 = 0;
    Delay_us(17800);
  }
}

   void Red11()
   {
    Red1=1;
    Yellow1=0;
    Green1=0;
   }
    void Yellow11()
   {
    Red1=0;
    Yellow1=1;
    Green1=0;
   }

       void Green11()
   {
    Red1=0;
    Yellow1=0;
    Green1=1;
   }

     void Red22()
   {
    Red2=1;
    Yellow2=0;
    Green2=0;
   }
    void Yellow22()
   {
    Red2=0;
    Yellow2=1;
    Green2=0;
   }

       void Green22()
   {
    Red2=0;
    Yellow2=0;
    Green2=1;
   }
   
 void ambulnce()
   {
    Red11();
    Red22();
     servoRotate0(); 

     servoRotate0_2(); 
    delay_ms(3000);
   }

void main()
{
  PORTB=0;
  TRISB = 0; 
 PORTC=0;
  TRISC=0XFF;
  
  
  servoRotate0(); 
  servoRotate0_2(); 

    Delay_ms(1000);
    servoRotate90(); 
  while(1)
  {
  

     Green11();
     Red22();
     servoRotate90_2(); 
     servoRotate0(); 
    while(DTMF1||DTMF2||DTMF3||DTMF4)
      {
        ambulnce();
      }
    Delay_ms(3000);

     Yellow11();
     Yellow22();
     servoRotate0_2(); 
     servoRotate90(); 
     
      while(DTMF1||DTMF2||DTMF3||DTMF4)
      {
        ambulnce();
      }
     Delay_ms(3000);

      Red11();
      Green22();
      Delay_ms(3000);

      Yellow11();
      Yellow22();
       servoRotate90_2(); 
      servoRotate0(); 
      
    while(DTMF1||DTMF2||DTMF3||DTMF4)
      {
        ambulnce();
      }
      Delay_ms(3000);

      Green11();
      Red22();
      while(DTMF1||DTMF2||DTMF3||DTMF4)
      {
        ambulnce();
      }
      Delay_ms(3000);
  }
}



