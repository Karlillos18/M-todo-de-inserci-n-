#include <iostream>

void imprimirArreglo(int arr[], int n) {
    for (int i = 0; i < n; ++i) {
        std::cout << arr[i] << " ";
    }
    std::cout << std::endl;
}

void ordenarPorInsercion(int arr[], int n, bool ascendente) {
    int i, key, j;
    for (i = 1; i < n; ++i) {
        key = arr[i];
        j = i - 1;

        
        if (ascendente) {
            while (j >= 0 && arr[j] > key) {
                arr[j + 1] = arr[j];
                --j;
            }
        } else {
            while (j >= 0 && arr[j] < key) {
                arr[j + 1] = arr[j];
                --j;
            }
        }
        arr[j + 1] = key;
    }
}

int main() {
    int arr[10];
    std::cout << "Ingrese 10 valores enteros separados por espacio: ";
    for (int i = 0; i < 10; ++i) {
        std::cin >> arr[i];
    }

    char opcion;
    std::cout << "¿Desea ordenar en orden ascendente (a) o descendente (d)? ";
    std::cin >> opcion;

    bool ascendente;
    if (opcion == 'a' || opcion == 'A') {
        ascendente = true;
    } else if (opcion == 'd' || opcion == 'D') {
        ascendente = false;
    } else {
        std::cerr << "Opción no válida. Saliendo del programa.\n";
        return 1;
    }

    ordenarPorInsercion(arr, 10, ascendente);

    std::cout << "Arreglo ordenado: ";
    imprimirArreglo(arr, 10);

    return 0;
}
