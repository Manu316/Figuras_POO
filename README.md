abstract class Figura {
    protected int numeroLados;

    public Figura(int numeroLados) {
        this.numeroLados = numeroLados;
    }

    public int getNumeroLados() {
        return numeroLados;
    }

    public abstract double obtenerArea();
    public abstract double obtenerPerimetro();
}


class Rectangulo extends Figura implements Redimensionar {
    private double base;
    private double altura;

    public Rectangulo(double base, double altura) {
        super(4);
        this.base = base;
        this.altura = altura;
    }

    @Override
    public double obtenerArea() {
        return base * altura;
    }

    @Override
    public double obtenerPerimetro() {
        return 2 * (base + altura);
    }

    @Override
    public void redimensionar(double factor) {
        this.base *= factor;
        this.altura *= factor;
    }
}

class Triangulo extends Figura {
    private double base;
    private double altura;

    public Triangulo(double base, double altura) {
        super(3);
        this.base = base;
        this.altura = altura;
    }

    @Override
    public double obtenerArea() {
        return 0.5 * base * altura;
    }

    @Override
    public double obtenerPerimetro() {
        return -1;
    }
}

interface Redimensionar {
    void redimensionar(double factor);
}

public class Figuras_POO {
    public static void main(String[] args) {
        Rectangulo rectangulo = new Rectangulo(4, 3);

        System.out.println("Área del rectángulo: " + rectangulo.obtenerArea());
        System.out.println("Perímetro del rectángulo: " + rectangulo.obtenerPerimetro());

        rectangulo.redimensionar(3);

        System.out.println("Nuevo área del rectángulo: " + rectangulo.obtenerArea());
        System.out.println("Nuevo perímetro del rectángulo: " + rectangulo.obtenerPerimetro());
        
        Triangulo triangulo = new Triangulo(4, 3);
        System.out.println("Área del triángulo: " + triangulo.obtenerArea());

    }
}
