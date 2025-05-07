import java.util.Scanner;

public class Ahorcado {
    // del 2 pero lo tomo como base Variables de instancia
    private String palabraSecreta;
    private char[] palabraOculta;
    private boolean[] letrasAdivinadas;
    private String[] dibujoAhorcado;
    private int intentosRestantes;

    // del 2 pero lo tomo como base Constructor e inicialización
    public Ahorcado(String palabraSecreta) {
        this.palabraSecreta = palabraSecreta.toUpperCase();
        this.palabraOculta = new char[palabraSecreta.length()];
        this.letrasAdivinadas = new boolean[palabraSecreta.length()];
        this.intentosRestantes = 6;
        inicializarPalabraOculta();
        inicializarDibujoAhorcado();
    }

    // Método principal del juego
    public void jugar() {
        Scanner sc = new Scanner(System.in);

        while (intentosRestantes > 0) {
            mostrarEstadoJuego();
            System.out.print("\nIngresa una letra: ");
            char letra = sc.next().toUpperCase().charAt(0);

            if (!validarCaracter(letra)) {
                intentosRestantes--;
                System.out.println("Letra incorrecta.");
            }

            if (validarPalabra(String.valueOf(palabraOculta), palabraSecreta)) {
                System.out.println("\n¡Felicidades! Has adivinado la palabra: " + palabraSecreta);
                return;
            }
        }

        // Si se acaban los intentos
        System.out.println(dibujoAhorcado[6]);
        System.out.println("¡Perdiste! La palabra era: " + palabraSecreta);
        sc.close();
    }

    // Verifica si la palabra fue adivinada completamente
    private boolean validarPalabra(String palabraOculta, String palabraSecreta) {
        return palabraOculta.equals(palabraSecreta);
    }

    //  Muestra el estado actual del juego
    private void mostrarEstadoJuego() {
        System.out.println("\nPalabra actual: " + String.valueOf(palabraOculta));
        System.out.println("Intentos restantes: " + intentosRestantes);
        System.out.println(dibujoAhorcado[6 - intentosRestantes]);
    }
    // falta cerrar el corchete para el ultimo que haga el juego no se olvide :)
