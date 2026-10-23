import java.util.Scanner;

public class Display_maquina{
    
public static void main (String[] args) {

    //Asignamos variables, arrays, etc...
    Scanner leer = new Scanner(System.in);
    int num = 9;
    String agotado = "AGOTADO";

    //Codigo para salir/seleccionar modo
    String codigo = "Especial";
    String codigosMaquina = "";
    String si_o_no_maquina = "Y";

    //Componentes asociados a maquina display

    //Arrays maquina base
    String maquina_productos [][] = new String [5][6];
    int maquina_cantidad_productos [][] = new int [5][6];
    String[] productos = {"Patatas","Monster","Chicles","Cerezas","Donetes"};
    
    //Arrays para guardar los productos de clientes
    int resta [][] = new int [5][6];
    String productos_elegidos [] = new String [270];

    //Lógica de la máquina
    boolean carritoActualizado = false;
    boolean buscando = false;
    boolean hayCarrito = false;
    boolean monedaValida = false;
    float moneda = 0;
    float tipos_monedas [] = {0.01f, 0.02f, 0.05f, 0.10f,0.50f,1,2};
    float monedas_en_maquina [] = new float [50];
    float cambio = 0;
    float total_dinero = 0;
    float total_precio = 0;
    String si_o_no_compra = "S";

    float[] coste = {1.2f,2.1f,5.6f,3.2f,4.2f}; 

    int contadorProductos = 0;
    String coordenadas_producto = "";
    boolean coordenada_encontrada = false;
    //Fin Componentes asociados a maquina
    //Modo mantenimiento
    boolean claveComprobar = false;
    int clave = 1492;
    int claveInput = 0;



//Comando salida
while(!codigo.equalsIgnoreCase("S")) {


while (codigo.equals("Especial")){ System.out.println("Modo visualizacion de maquina (G),Modo de compra (C), Modo Mantenimiento (M), Salir del programa (S)");
System.out.print("Escribe un modo: ");
codigo = leer.nextLine();
        }


//Validación de códigos
if (codigo.equalsIgnoreCase("G")) {
}else if (codigo.equalsIgnoreCase("Especial")) {
}else if (codigo.equalsIgnoreCase("S")){
}else if (codigo.equalsIgnoreCase("C")){
}else if (codigo.equalsIgnoreCase("M")){
}else{
System.out.println("Error al selecionar el modo, esa letra no tiene funcion.");
codigo = "Especial";
}

 //Detecta si el la el modo está en ver maquina
        while (codigo.equalsIgnoreCase("G")) {
            
            //Pregunta si se desea cambiar de modo
            System.out.println("Escribe un modo de vista de maquina (C) cantidad, (P) Posiciones, (M) Muestra los productos");
            codigosMaquina = leer.nextLine();

            //Funcion de mostrar cantidad de productos
            if (codigosMaquina.equalsIgnoreCase("C")) {
                for (int i = 0; i < maquina_cantidad_productos.length; i++) {
                    for (int j = 0; j < maquina_cantidad_productos[i].length; j++) {
                        maquina_cantidad_productos[i][j] = num - resta [i][j]; 
                    }
                }
        
                //Función de print de maquina
                System.out.println(" -------------------------");
                System.out.println(" |      ALIMENTACION     |");
                System.out.println(" -------------------------");

                //Añadir decoraciones

                for (int i = 0; i < maquina_cantidad_productos.length; i++) {
                    for (int j = 0; j < maquina_cantidad_productos[i].length; j++) {
                        System.out.print(" | ");
                        System.out.print(maquina_cantidad_productos [i][j]);
                }

                //Elementos que se repiten (Recursivos)
                System.out.print(" | ");
                System.out.println(" ");
                System.out.println(" -------------------------");
                }
                //Finalización cajetín de debajo
                System.out.println(" |                       |");
                System.out.println(" -------------------------");

                //Espera de 5 segundos para que el usuario vea cuantos productos hay y evita spam
                try {
                    Thread.sleep(500);
                    } catch (InterruptedException e) {
                        System.out.println("Espera interrumpida");
                    }
                    
            //Si el usuario quiere salir que escriba una letra diferente
            System.out.println("¿Desea continuar? Si (S) / No (N) ");
            si_o_no_maquina = leer.nextLine();

            //Analiza si se quiere salir
            if (si_o_no_maquina.equalsIgnoreCase("S")) {
            }else{
                si_o_no_maquina = "N";
                codigosMaquina = "L";
                codigo = "Especial";
            }

        //Cierra el primer caso del codigoMaquina (C)
            }
        
            //Funcion de mostrar identificadores
            if (codigosMaquina.equalsIgnoreCase("P")) {
        
                //Función de print de maquina
                System.out.println(" -------------------------------");
                System.out.println(" |         ALIMENTACION        |");
                System.out.println(" -------------------------------");

                //Añadir decoraciones

                for (int i = 0; i < maquina_cantidad_productos.length; i++) {
                    for (int j = 0; j < maquina_cantidad_productos[i].length; j++) {
                        System.out.print(" | ");
                        System.out.print((char)('B' + i) + "" + (j + 1));
                }

                //Elementos que se repiten (Recursivos)
                System.out.print(" | ");
                System.out.println(" ");
                System.out.println(" -------------------------------");
                }
                //Finalización cajetín de debajo
                System.out.println(" |                             |");
                System.out.println(" -------------------------------");

                //Espera de 5 segundos para que el usuario vea cuantos productos hay y evita spam
                try {
                    Thread.sleep(500);
                    } catch (InterruptedException e) {
                        System.out.println("Espera interrumpida");
                    }
                    //Si el usuario quiere salir que escriba una letra diferente

            System.out.println("Continuar Si (S) / No (N) ");
            si_o_no_maquina = leer.nextLine();

            //Analiza si se quiere salir
            if (si_o_no_maquina.equalsIgnoreCase("S")) {
            }else{
                si_o_no_maquina = "N";
                codigosMaquina = "L";
                codigo = "Especial";
            }
        //Cierra el modo de posiciones (P)
            }
          
            //Muestra los productos
            if (codigosMaquina.equalsIgnoreCase("M")) {

                //Print para que pueda ver si está fuera de stock
                for (int i = 0; i < maquina_cantidad_productos.length; i++) {
                    for (int j = 0; j < maquina_cantidad_productos[i].length; j++) {
                        maquina_cantidad_productos[i][j] = num - resta [i][j]; 
                    }
                }

                for (int i = 0; i < maquina_productos.length; i++) {
                    for (int j = 0; j < maquina_productos[i].length; j++) {
                        maquina_productos [i][j] = productos [i];
                            if (maquina_cantidad_productos [i][j] <= 0) {
                                maquina_productos [i][j] = agotado;
                            }
                    }
                }
                
        
                //Función de print de maquina
                System.out.println(" -------------------------------------------------------------");
                System.out.println(" |                        ALIMENTACION                       |");
                System.out.println(" -------------------------------------------------------------");

                //Añadir decoraciones

                for (int i = 0; i < maquina_productos.length; i++) {
                    for (int j = 0; j < maquina_productos[i].length; j++) {
                        System.out.print(" | ");
                        System.out.print(maquina_productos [i][j]);
                }

                //Elementos que se repiten (Recursivos)
                System.out.print(" | ");
                System.out.println(" ");
                System.out.println(" -------------------------------------------------------------");
                }
                //Finalización cajetín de debajo
                System.out.println(" |                                                           |");
                System.out.println(" -------------------------------------------------------------");

                //Espera de 5 segundos para que el usuario vea cuantos productos hay y evita spam
                try {
                    Thread.sleep(500);
                    } catch (InterruptedException e) {
                        System.out.println("Espera interrumpida");
                    }
                    //Si el usuario quiere salir que escriba una letra diferente

            System.out.println("Continuar Si (S) / No (N) ");
            si_o_no_maquina = leer.nextLine();

            //Analiza si se quiere salir
            if (si_o_no_maquina.equalsIgnoreCase("S")) {
            }else{
                si_o_no_maquina = "N";
                codigosMaquina = "L";
                codigo = "Especial";
            }
        
        //Cierra el modo de muestra de productos (M)
        }
        //Cierra el modo de vista de maquina (G)
        }

        //Modo de compra (C)
        while (codigo.equalsIgnoreCase("C")) {

            //Hace un print de la maquina productos para poder ver los productos
            for (int i = 0; i < maquina_productos.length; i++){
                for (int j = 0; j < maquina_productos[i].length; j++) {
                    maquina_productos [i][j] = productos [i];
                }
            }

            for (int i = 0; i < maquina_cantidad_productos.length && buscando; i++) {
                    for (int j = 0; j < maquina_cantidad_productos[i].length; j++) {
                        maquina_cantidad_productos[i][j] = num - resta [i][j]; 
                        if (maquina_cantidad_productos [i][j] <= 0) {
                            maquina_productos [i][j] = agotado;
                        }
                    }
                }

             //Pregunta si se desea cambiar de modo
             System.out.println("Elegir producto/s (E), Insertar dinero (D), Pagar con tarjeta (T), Carrito (C)");
             codigosMaquina = leer.nextLine();

                //Modo para elegir productos (E)
                if (codigosMaquina.equalsIgnoreCase("E")) {
                    System.out.println("Escribe las coordenadas del producto: ");
                    coordenadas_producto = leer.nextLine();

                    //Verifica si la coordenada escrita se encuentra en la lista de coordenadas
                    for (int i = 0; i < maquina_cantidad_productos.length; i++) {

                        for (int j = 0; j < maquina_cantidad_productos[i].length; j++) {
                            String coordenada = (char) ('B' + i) + "" + (j + 1);

                            if (coordenadas_producto.equalsIgnoreCase(coordenada)) {
                                hayCarrito = true;
                                coordenada_encontrada = true;

                            
                            System.out.println("Confirmar producto " + maquina_productos [i][j] + " S (S) / N (N)");
                            
                                si_o_no_compra = leer.nextLine();

                                    if(si_o_no_compra.equalsIgnoreCase("S")) {
                                        if (contadorProductos < productos_elegidos.length) {
                                            productos_elegidos[contadorProductos] = maquina_productos[i][j];
                                            contadorProductos++;
                                            carritoActualizado = true;
                                        }else{
                                            System.out.println("El carrito está lleno");
                                        }
                                    }

                            }else{
                               
                            }
                            
                        

                        } 
                        
                         
                    }
                    
                    
                    //Espera de 5 segundos para que el usuario vea cuantos productos hay y evita spam
                    try {
                        Thread.sleep(500);
                        } catch (InterruptedException e) {
                        System.out.println("Espera interrumpida");
                        }
            
                    //Si el usuario quiere salir que escriba una letra diferente
                    System.out.println("Continuar Si (S) / No (N) ");
                    si_o_no_maquina = leer.nextLine();

                    //Analiza si se quiere salir
                    if (si_o_no_maquina.equalsIgnoreCase("S")) {
                    }else{
                        si_o_no_maquina = "N";
                        codigosMaquina = "L";
                        codigo = "Especial";
                    }

                 //Cierre modo elegir productos (E)
                }
                

                //Modo insertar dinero
                while (codigosMaquina.equalsIgnoreCase("D")) {
                    
                    if (hayCarrito == true) {

                        System.out.println("Monedas que acepta la maquina: 0,1, 0,2, 0,5, 1, 2 euros");
                        System.out.println("Ingrese las monedas:");
                        moneda = leer.nextFloat();

                        for (int i = 0; i < tipos_monedas.length; i++){
                            if (moneda == tipos_monedas [i]) {
                            monedaValida = true;
                            }else{}
                        }
                    
                        if (monedaValida == false){
                            System.out.print("Moneda no valida, solo se pueden meter monedas de 10 centimos o más. Asegurese de no poner el simbolo de €");
                        }

                        System.out.println(moneda);

                  
                        if (monedaValida == true) {
                            total_dinero = total_dinero + moneda;
                            System.out.println("Dinero metido:" + total_dinero);
                            System.out.println(total_precio - total_dinero);
                            monedaValida = false;
                        }
                    
                    //Cuando te pases del dinero te impide meter más

                    //Comprobar carrito
                        }else{
                            System.out.println("No hay carrito");
                            break;
                        }
                    
                        if (total_dinero >= total_precio && total_precio != 0) {
                            codigosMaquina = "";
                            codigo = "Especial";
                            System.out.println("Pago completado");
                            hayCarrito = false;
                        }

                    //Cierre modo insertar dinero 
                }

                //Modo pagar con tarjeta
                if (codigosMaquina.equalsIgnoreCase("T")) {

            //Cierre modo pagar con tarjeta
                }

                //Modo carrito
                if (codigosMaquina.equalsIgnoreCase("C")) {
                    
                    if (carritoActualizado == true) {
                        for (int i = 0; i < productos.length; i++) {
                            if (productos [i].equals(productos_elegidos [i])){
                                total_precio = total_precio + coste [i];
                            }
                        }
                        carritoActualizado = false;
                    }

                    if (hayCarrito == true) {
                    for (int i = 0 ; i < contadorProductos; i++) {
                    System.out.println(productos_elegidos[i]);
                    }

                    System.out.println("El precio es de " + total_precio + " euros.");

                    }

                    if (hayCarrito == false)
                        System.out.println("No hay carrito");

                    //Cierre modo carrito
                    }
            
            
            
             //Cierre modo compra (C)
            }

        while (codigo.equalsIgnoreCase("M")) {
            
            if (claveComprobar == false) {
            System.out.print("Escribe la clave para poder continuar: ");
            claveInput = leer.nextInt(); 
            leer.nextLine();

                if (clave == claveInput) {
                    System.out.println("Acceso concedido");
                    claveComprobar = true;
                }
            }

            while(claveComprobar == true) {
                System.out.print("Modo reponer (R), Modo ajuste de precios (A), Modo de monedas (M)");
                codigosMaquina = leer.nextLine();

                if (codigosMaquina.equalsIgnoreCase("R")) {
                    
                }
                
                if (codigosMaquina.equalsIgnoreCase("A")) {
                    
                }

                if (codigosMaquina.equalsIgnoreCase("M")) {
                    
                }

            }
           

            

         //Cerrar modo admin
        }

        

        
         //Cierra While Salir (S)
        }
        //Cierra args
     }
   
        //Cierra main
}
