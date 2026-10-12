# Work
Aplicación simple
/******************************************************************************
 * SISTEMA DE GESTIÓN DE PRODUCTOS
 * Código optimizado para Compiladores y Depuradores en línea (OnlineGDB)
 *******************************************************************************/

// ============================================================================
// 1. CLASE PRODUCTO (Plantilla del Objeto)
// ============================================================================
class Producto {
    // Atributos de la clase
    private String id;
    private String nombre;
    private double precio;
    private int cantidadStock;

    // Constructor para inicializar los atributos
    public Producto(String id, String nombre, double precio, int cantidadStock) {
        this.id = id;
        this.nombre = nombre;
        this.precio = precio;
        this.cantidadStock = cantidadStock;
    }

    // Método para agregar stock
    public void agregarStock(int cantidad) {
        if (cantidad > 0) {
            this.cantidadStock += cantidad;
            System.out.println(" Stock actualizado. Se sumaron " + cantidad + " unidades a: " + this.nombre);
        } else {
            System.out.println("❌ Error: La cantidad debe ser mayor a cero.");
        }
    }

    // Método para vender un producto (reduce stock)
    public boolean vender(int cantidad) {
        if (cantidad <= this.cantidadStock) {
            this.cantidadStock -= cantidad;
            System.out.println(" Venta exitosa: " + cantidad + " unidad(es) de " + this.nombre);
            return true;
        } else {
            System.out.println("❌ Error: Stock insuficiente para vender " + cantidad + " unidades de " + this.nombre);
            return false;
        }
    }

    // Método para imprimir la información en consola
    public void mostrarInformacion() {
        System.out.println("----------------------------------------");
        System.out.println("ID del Producto : " + this.id);
        System.out.println("Nombre          : " + this.nombre);
        System.out.println("Precio          : $" + this.precio);
        System.out.println("Stock Disponible: " + this.cantidadStock + " unidades");
        System.out.println("----------------------------------------");
    }
}

// ============================================================================
// 2. CLASE PRINCIPAL (Punto de entrada de OnlineGDB)
// ============================================================================
public class Main {
    public static void main(String[] args) {
        
        System.out.println("=== INICIANDO SISTEMA DE GESTIÓN DE PRODUCTOS ===\n");

        // INSTANCIACIÓN DE OBJETOS
        Producto prod1 = new Producto("P001", "Laptop ASUS Zephyrus", 1250.00, 10);
        Producto prod2 = new Producto("P002", "Mouse Logi MX Master 3", 99.99, 25);

        // PRUEBA DE MÉTODOS
        System.out.println("--- Inventario Inicial ---");
        prod1.mostrarInformacion();
        prod2.mostrarInformacion();

        System.out.println("\n--- Procesando Ventas ---");
        prod1.vender(3);  // Debe tener éxito (quedan 7)
        prod2.vender(30); // Debe fallar por falta de stock

        System.out.println("\n--- Actualizando Inventario ---");
        prod2.agregarStock(15); // Añade 15 unidades (total 40)
        prod2.vender(30);       // Ahora sí debe completarse la venta (quedan 10)

        System.out.println("\n--- Inventario Final ---");
        prod1.mostrarInformacion();
        prod2.mostrarInformacion();
    }
}
