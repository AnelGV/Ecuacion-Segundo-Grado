import java.util.Random;

public class GenerarDatos {
    // Arrays con datos ficticios para nombres y apellidos
    private static final String[] nombres = {
        "Juan", "María", "Carlos", "Laura", "Ana", "Pedro", "Sofía", "Luis", "Valentina", "Diego"
    };
    private static final String[] apellidos = {
        "González", "Rodríguez", "López", "Fernández", "Martínez", "Pérez", "Gómez", "Díaz", "Torres", "Hernández"
    };

    // Método para generar un número aleatorio de 1000000000 a 9999999999
    private static String generarTelefono() {
        Random rand = new Random();
        int numero = 100000000 + rand.nextInt(900000000);
        return "9" + numero; // Prefijo 9 para simular un teléfono
    }

    // Método principal
    public static void main(String[] args) {
        Random random = new Random();
        
        for (int i = 1; i <= 100; i++) {
            // Generar datos aleatorios
            String nombre = nombres[random.nextInt(nombres.length)];
            String apellido = apellidos[random.nextInt(apellidos.length)];
            String correo = nombre.toLowerCase() + "." + apellido.toLowerCase() + "@ejemplo.com";
            String telefono = generarTelefono();

            // Crear la consulta SQL de inserción
            String sql = String.format(
                "INSERT INTO usuarios (id, nombre, apellido, correo, telefono) VALUES (%d, '%s', '%s', '%s', '%s');",
                i, nombre, apellido, correo, telefono
            );

            // Mostrar la consulta SQL
            System.out.println(sql);
        }
    }
}

