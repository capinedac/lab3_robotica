# Laboratorio 3 - Robótica Industrial 2, Entradas y Salidas
Equipo de trabajo: 
- Luis Alberto Chavez Castro
- Camilo Pineda Correa

## Desarrollo de solución

Para este laboratorio, se utilizo el código desarrollado en el laboratorio 1, el cual realizaba la escritura de 2 letras en un plano inclinado. En esta ocación se pedia realizar 2 ejecuciones del robot ABB a través del accionamiento de entradas digitales desde una caja de entradas y salidas conectada al controlador.

El accionamiento del primer boton encendia un led o salida digital y ejecutaba la rutina para la escritura de las letras, mientras que el accionamiento del segundo botón apagaba el mismo led y ejecutaba una nueva rutina que posiciona al robot en una pose que permite colocar o retirar la herramienta del plato portaherramientas.

Esto se realizo generando 2 entradas digitales (2 botones para las rutinas) y 1 salida digital (led de encendido y apagado según rutina) nuevas en el programa. Estas se enlazan con las DI y DO fisicas del controlador con ayuda del Flex pendant, el cual modifica el nombre de la variable para ser reconocidas. Es importante ayudarse de esta herramienta para identificar el funcionamiento de las DI y DO antes de utilizarlas. Luego el codigo es ejecutado, donde el robot ABB no realiza ningun proceso al mantenerse en espera a la entrada digital.

La espera al accionamiento de una entrada digital se logra con la funcion 'WaitDI', y para la modificación de una salida digital se utiliza 'SetDO'. 


## Código Rapid
```rapid
PROC main()
        !Add your code here
        WaitDI EntDI_1,1;
        SetDO SalDO_1,1;
        MyHomePath;
        MyClosePath;
        Letra_L;
        Letra_C;
        MyClosePath;
        MyHomePath;
        WaitDI EntDI_2,1;
        SetDO SalDO_1,0;
        MyToolPath;
    ENDPROC
    PROC Letra_L()
        MoveL Target_10,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_20,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_30,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_40,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_50,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_60,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_70,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_80,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_90,v200,z5,Marcador_LC\WObj:=Plano45;
    ENDPROC
    PROC Letra_C()
        MoveL Target_100,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_110,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_120,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_130,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_140,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_150,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_160,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_170,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_180,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_190,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_200,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_210,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_220,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_230,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_240,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_250,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_260,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_270,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_280,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_290,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_300,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_310,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_320,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_330,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_340,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_350,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_360,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_370,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_380,v200,z5,Marcador_LC\WObj:=Plano45;
        MoveL Target_390,v200,z5,Marcador_LC\WObj:=Plano45;
    ENDPROC
    PROC MyHomePath()
        !WaitDI EntDI_2,1;
        !SetDO SalDO_2,1;
        MoveAbsJ MyHome_LC,v200,z5,Marcador_LC\WObj:=Plano45;
    ENDPROC
    PROC MyClosePath()
        !WaitDI EntDI_1,1;
        !SetDO SalDO_1,1;
        MoveAbsJ MyClose_LC,v200,z5,Marcador_LC\WObj:=Plano45;
    ENDPROC
    PROC MyToolPath()
        MoveAbsJ MyTool_LC,v200,z5,Marcador_LC\WObj:=Plano45;
    ENDPROC
```


## Conclusiones
* La implementación de entradas digitales y salidas digitales facilita el uso de un robot como este por parte de un usuario que llegue a estar poco familiarizado, ya sea con su funcionamiento u operación desde un Flex pendant.
* Es importante identificar el funcionamiento de las DI y DO físicas utilizadas en el código, de esta forma se descarta que el error en su pulsado o seteado sea o no del código, a cambio de ser por malfuncionamiento.

