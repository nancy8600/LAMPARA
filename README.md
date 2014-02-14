LAMPARA
=======

CODIGO DE LAMPARA EN ARDUINO
#define maxleds 8 //creamos la variable maxleds de 8 elementos
#define pot1 A0 //creamos la variable pot con el pin A1
#define pot2 A1 //creamos la variable pot con el pin A2

int led[maxleds] = {2,3,4,5,6,7,8,9}; //creamos un vector para los pines a utilizar

void setup ()
{
 Serial.begin(9600);
 for (int i=0;i<maxleds;i++)
 pinMode(led[i],OUTPUT); // Los pines del 2 al 9 seran de salida
}

void loop()
{

 for (int i=0;i<=maxleds;i++)
 {
 int timeon = analogRead(pot1); // lee el valor del potenciometro 1
 int t1=map(timeon, 0, 1023, 0, 2000); // hace un mapeo o conversion
 int timeoff = analogRead(pot2); // lee el valor del potenciometro 2
 int t2=map(timeoff, 0, 1023, 0, 2000); // hace un mapeo o conversion
 prender(led[i],t1); //llama a la funcion prender ingresando los parametros
 apagar(led[i],t2); //llama a la funcion apagar ingresando los parametros
 }

 for (int i=maxleds;i>=0;i--)
 {
 int timeon = analogRead(pot1); // lee el valor del potenciometro 1
 int t1=map(timeon, 0, 1023, 0, 2000); // hace un mapeo o conversion
 int timeoff = analogRead(pot2); // lee el valor del potenciometro 2
 int t2=map(timeoff, 0, 1023, 0, 2000); // hace un mapeo o conversion
 prender(led[i],t1); //llama a la funcion prender ingresando los parametros
 apagar(led[i],t2); //llama a la funcion apagar ingresando los parametros
 }

}

void prender(int i, int t) //funcion para enceder el led
{
 digitalWrite(i, HIGH);//led esta encendido
 delay(t); //tiempo de encendido
}

void apagar(int i, int t)
{
 digitalWrite(i, LOW);//led esta apagado
 delay(20); //tiempo de apagado
}
