# Vetores e Matrizes em C: 20 Exemplos para Iniciantes

Este documento contém 20 exemplos de vetores e matrizes na linguagem de programação **C**, com explicações detalhadas para pessoas leigas. Cada exemplo inclui:

- **Código comentado**: Explicação linha por linha.
- **Lógica por trás**: O que o código faz e por que é útil.
- **Saída esperada**: O que aparece na tela ao executar o programa.

Os exemplos progridem de conceitos simples (vetores) a mais complexos (matrizes). Copie os códigos manualmente para fixar o aprendizado e teste-os em um compilador C (como GCC, Dev-C++, ou OnlineGDB).

---

## O que são vetores e matrizes?

- **Vetor**: Uma lista de "caixinhas" na memória, cada uma com um valor (ex.: números, como `{1, 2, 3}`).
- **Matriz**: Uma tabela com linhas e colunas, como uma planilha (ex.: `{{1, 2}, {3, 4}}`).
- **Array**: Nome geral para vetores (1 dimensão) e matrizes (2 ou mais dimensões).

**Nota**: Em C, arrays têm tamanho fixo definido na criação, e usamos a biblioteca `stdio.h` para entrada/saída.

---

## Exemplo 1: Criando um vetor simples

```c
#include <stdio.h>

int main() {
    // Criando um vetor com 5 números
    int numeros[5] = {1, 2, 3, 4, 5};
    
    // Mostrando o vetor
    printf("Vetor: ");
    for (int i = 0; i < 5; i++) {
        printf("%d ", numeros[i]);
    }
    printf("\n");
    
    return 0;
}
```

### Explicação
- `#include <stdio.h>`: Inclui a biblioteca para usar `printf` (mostrar na tela).
- `int main()`: Onde o programa começa.
- `int numeros[5] = {1, 2, 3, 4, 5};`: Cria um vetor com 5 números inteiros.
- `for (int i = 0; i < 5; i++)`: Conta de 0 a 4 (índices do vetor).
- `printf("%d ", numeros[i])`: Mostra cada número.
- `printf("\n")`: Pula uma linha.
- `return 0`: Finaliza o programa.

### Lógica
Cria e exibe uma lista de números. Útil para armazenar sequências, como notas ou idades.

### Saída
```
Vetor: 1 2 3 4 5
```

---

## Exemplo 2: Acessando elementos de um vetor

```c
#include <stdio.h>

int main() {
    // Criando um vetor de números
    int numeros[3] = {10, 20, 30};
    
    // Mostrando elementos específicos
    printf("Primeiro número: %d\n", numeros[0]);
    printf("Segundo número: %d\n", numeros[1]);
    
    return 0;
}
```

### Explicação
- `int numeros[3] = {10, 20, 30};`: Cria um vetor com 3 números.
- `numeros[0]`: Acessa o primeiro número (índice 0).
- `numeros[1]`: Acessa o segundo número (índice 1).
- `printf`: Mostra os valores.

### Lógica
Usa índices (0, 1, 2...) para acessar valores específicos. Útil para buscar itens, como o primeiro nome em uma lista.

### Saída
```
Primeiro número: 10
Segundo número: 20
```

---

## Exemplo 3: Alterando um elemento no vetor

```c
#include <stdio.h>

int main() {
    // Criando um vetor
    int notas[3] = {7, 8, 9};
    
    // Alterando a primeira nota
    notas[0] = 10;
    
    // Mostrando o vetor
    printf("Notas: ");
    for (int i = 0; i < 3; i++) {
        printf("%d ", notas[i]);
    }
    printf("\n");
    
    return 0;
}
```

### Explicação
- `int notas[3] = {7, 8, 9};`: Cria um vetor com 3 notas.
- `notas[0] = 10;`: Muda o primeiro valor para 10.
- `for`: Mostra todos os valores.

### Lógica
Muda valores usando índices. Útil para corrigir dados, como uma nota errada.

### Saída
```
Notas: 10 8 9
```

---

## Exemplo 4: Lendo valores para um vetor

```c
#include <stdio.h>

int main() {
    // Criando um vetor
    int numeros[3];
    
    // Lendo valores
    for (int i = 0; i < 3; i++) {
        printf("Digite o número %d: ", i + 1);
        scanf("%d", &numeros[i]);
    }
    
    // Mostrando o vetor
    printf("Vetor: ");
    for (int i = 0; i < 3; i++) {
        printf("%d ", numeros[i]);
    }
    printf("\n");
    
    return 0;
}
```

### Explicação
- `int numeros[3];`: Cria um vetor vazio com espaço para 3 números.
- `for`: Laço para ler 3 valores.
- `scanf("%d", &numeros[i]);`: Lê um número do usuário e armazena no vetor.
- `for`: Mostra o vetor.

### Lógica
Permite que o usuário preencha o vetor. Útil para criar listas personalizadas, como notas.

### Saída (exemplo com entradas 1, 2, 3)
```
Digite o número 1: 1
Digite o número 2: 2
Digite o número 3: 3
Vetor: 1 2 3
```

---

## Exemplo 5: Tamanho de um vetor

```c
#include <stdio.h>

int main() {
    // Criando um vetor
    int cores[4] = {1, 2, 3, 4};
    
    // Calculando o tamanho
    int tamanho = sizeof(cores) / sizeof(cores[0]);
    
    // Mostrando o tamanho
    printf("Número de elementos: %d\n", tamanho);
    
    return 0;
}
```

### Explicação
- `int cores[4] = {1, 2, 3, 4};`: Cria um vetor com 4 números.
- `sizeof(cores)`: Calcula o tamanho total do vetor em bytes.
- `sizeof(cores[0])`: Calcula o tamanho de um elemento.
- `tamanho = sizeof(cores) / sizeof(cores[0])`: Divide para obter o número de elementos.
- `printf`: Mostra o tamanho.

### Lógica
Conta quantos elementos estão no vetor. Útil para saber o tamanho de uma lista.

### Saída
```
Número de elementos: 4
```

---

## SIXTH EXAMPLE: LOOPING THROUGH A VECTOR

```c
#include <stdio.h>

int main() {
    // Creating a vector
    int numbers[3] = {10, 20, 30};
    
    // Displaying each number
    for (int i = 0; i < 3; i++) {
        printf("Number %d: %d\n", i + 1, numbers[i]);
    }
    
    return 0;
}
```

### Explanation
- `int numbers[3] = {10, 20, 30};`: Creates a vector with 3 numbers.
- `for`: Loops through each index (0 to 2).
- `printf`: Displays each number with its position (adjusted to start at 1 for the user).

### Logic
Shows each element in the vector. Useful for listing items, such as names in a list.

### Output
```
Number 1: 10
Number 2: 20
Number 3: 30
```

---

## SEVENTH EXAMPLE: SUMMING VECTOR ELEMENTS

```c
#include <stdio.h>

int main() {
    // Creating a vector
    int values[4] = {5, 10, 15, 20};
    
    // Variable to store the sum
    int sum = 0;
    
    // Summing
    for (int i = 0; i < 4; i++) {
        sum += values[i];
    }
    
    // Displaying the sum
    printf("Sum of values: %d\n", sum);
    
    return 0;
}
```

### Explanation
- `int values[4] = {5, 10, 15, 20};`: Creates a vector with 4 numbers.
- `int sum = 0;`: Variable to store the sum.
- `for`: Adds each element to `sum`.
- `printf`: Shows the total.

### Logic
Sums all values in the vector. Useful for calculating totals, like prices or grades.

### Output
```
Sum of values: 50
```

---

## EIGHTH EXAMPLE: FINDING THE LARGEST VALUE IN A VECTOR

```c
#include <stdio.h>

int main() {
    // Creating a vector
    int numbers[5] = {4, 7, 2, 9, 1};
    
    // Starting with the first number
    int largest = numbers[0];
    
    // Checking each number
    for (int i = 1; i < 5; i++) {
        if (numbers[i] > largest) {
            largest = numbers[i];
        }
    }
    
    // Displaying the largest
    printf("Largest number: %d\n", largest);
    
    return 0;
}
```

### Explanation
- `int numbers[5] = {4, 7, 2, 9, 1};`: Creates a vector with 5 numbers.
- `int largest = numbers[0];`: Assumes the first number is the largest.
- `for`: Compares each number with `largest`, updating if a larger number is found.
- `printf`: Shows the largest number.

### Logic
Finds the largest value in the vector. Useful for finding the highest price or grade.

### Output
```
Largest number: 9
```

---

## NINTH EXAMPLE: CREATING A SIMPLE MATRIX

```c
#include <stdio.h>

int main() {
    // Creating a 2x3 matrix
    int matrix[2][3] = {{1, 2, 3}, {4, 5, 6}};
    
    // Displaying the matrix
    printf("Matrix:\n");
    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 3; j++) {
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }
    
    return 0;
}
```

### Explanation
- `int matrix[2][3] = {{1, 2, 3}, {4, 5, 6}};`: Creates a matrix with 2 rows and 3 columns.
- `for (int i = 0; i < 2; i++)`: Loops through each row.
- `for (int j = 0; j < 3; j++)`: Loops through each column.
- `printf("%d ", matrix[i][j])`: Displays the element at row `i`, column `j`.
- `printf("\n")`: Adds a new line after each row.

### Logic
Displays a matrix as a table. Useful for organizing data, like grades for different tests.

### Output
```
Matrix:
1 2 3
4 5 6
```

---

## TENTH EXAMPLE: ACCESSING MATRIX ELEMENTS

```c
#include <stdio.h>

int main() {
    // Creating a 2x2 matrix
    int matrix[2][2] = {{10, 20}, {30, 40}};
    
    // Displaying a specific element
    printf("Element [0][1]: %d\n", matrix[0][1]);
    
    return 0;
}
```

### Explanation
- `int matrix[2][2] = {{10, 20}, {30, 40}};`: Creates a 2x2 matrix.
- `matrix[0][1]`: Accesses the element at row 0, column 1 (20).
- `printf`: Shows the value.

### Logic
Accesses specific values in a matrix using two indices. Useful for retrieving data from tables.

### Output
```
Element [0][1]: 20
```

---

## ELEVENTH EXAMPLE: MODIFYING A MATRIX ELEMENT

```c
#include <stdio.h>

int main() {
    // Creating a 2x2 matrix
    int matrix[2][2] = {{1, 2}, {3, 4}};
    
    // Modifying an element
    matrix[1][0] = 99;
    
    // Displaying the matrix
    printf("Updated matrix:\n");
    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 2; j++) {
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }
    
    return 0;
}
```

### Explanation
- `int matrix[2][2] = {{1, 2}, {3, 4}};`: Creates a 2x2 matrix.
- `matrix[1][0] = 99;`: Changes the value at row 1, column 0.
- `for`: Displays the updated matrix.

### Logic
Changes values in a matrix using indices. Useful for correcting data in tables.

### Output
```
Updated matrix:
1 2
99 4
```

---

## TWELFTH EXAMPLE: SUMMING MATRIX ELEMENTS

```c
#include <stdio.h>

int main() {
    // Creating a 2x2 matrix
    int matrix[2][2] = {{1, 2}, {3, 4}};
    
    // Variable to store the sum
    int sum = 0;
    
    // Summing elements
    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 2; j++) {
            sum += matrix[i][j];
        }
    }
    
    // Displaying the sum
    printf("Sum of elements: %d\n", sum);
    
    return 0;
}
```

### Explanation
- `int matrix[2][2] = {{1, 2}, {3, 4}};`: Creates a 2x2 matrix.
- `int sum = 0;`: Variable to store the sum.
- `for`: Nested loops to sum each element.
- `sum += matrix[i][j]`: Adds the element to the sum.
- `printf`: Shows the total.

### Logic
Sums all values in a matrix. Useful for calculating totals in tables.

### Output
```
Sum of elements: 10
```

---

## THIRTEENTH EXAMPLE: READING A MATRIX FROM USER INPUT

```c
#include <stdio.h>

int main() {
    // Creating a 2x2 matrix
    int matrix[2][2];
    
    // Reading values
    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 2; j++) {
            printf("Enter value for [%d][%d]: ", i, j);
            scanf("%d", &matrix[i][j]);
        }
    }
    
    // Displaying the matrix
    printf("Matrix:\n");
    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 2; j++) {
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }
    
    return 0;
}
```

### Explanation
- `int matrix[2][2];`: Creates an empty 2x2 matrix.
- `for`: Loops to read values for each position.
- `scanf`: Reads a number from the user.
- `for`: Displays the matrix.

### Logic
Allows the user to create a matrix with custom values. Useful for personalized tables.

### Output (example with inputs 1, 2, 3, 4)
```
Enter value for [0][0]: 1
Enter value for [0][1]: 2
Enter value for [1][0]: 3
Enter value for [1][1]: 4
Matrix:
1 2
3 4
```

---

## FOURTEENTH EXAMPLE: CHECKING IF A NUMBER IS IN A VECTOR

```c
#include <stdio.h>

int main() {
    // Creating a vector
    int numbers[4] = {5, 10, 15, 20};
    
    // Reading the number to search
    int search;
    printf("Enter a number to search: ");
    scanf("%d", &search);
    
    // Checking
    int found = 0;
    for (int i = 0; i < 4; i++) {
        if (numbers[i] == search) {
            found = 1;
            break;
        }
    }
    
    // Displaying the result
    if (found) {
        printf("The number %d is in the vector!\n", search);
    } else {
        printf("The number %d is not in the vector.\n", search);
    }
    
    return 0;
}
```

### Explanation
- `int numbers[4] = {5, 10, 15, 20};`: Creates a vector.
- `scanf`: Reads the number to search.
- `int found = 0;`: Variable to indicate if the number was found.
- `for`: Checks each element.
- `if`: If the number is found, sets `found` to 1 and exits the loop (`break`).
- `printf`: Shows the result.

### Logic
Checks if a number is in the vector. Useful for searches, like finding a student in a list.

### Output (example with input 10)
```
Enter a number to search: 10
The number 10 is in the vector!
```

---

## FIFTEENTH EXAMPLE: COUNTING EVEN NUMBERS IN A VECTOR

```c
#include <stdio.h>

int main() {
    // Creating a vector
    int numbers[5] = {1, 2, 3, 4, 5};
    
    // Counter for even numbers
    int count = 0;
    
    // Checking
    for (int i = 0; i < 5; i++) {
        if (numbers[i] % 2 == 0) {
            count++;
        }
    }
    
    // Displaying the result
    printf("Even numbers: %d\n", count);
    
    return 0;
}
```

### Explanation
- `int numbers[5] = {1, 2, 3, 4, 5};`: Creates a vector.
- `int count = 0;`: Variable to count even numbers.
- `if (numbers[i] % 2 == 0)`: Checks if the number is divisible by 2 (even).
- `count++`: Increments the counter.
- `printf`: Shows the total.

### Logic
Counts even numbers in the vector. Useful for statistics.

### Output
```
Even numbers: 2
```

---

## SIXTEENTH EXAMPLE: MULTIPLYING VECTOR ELEMENTS BY 2

```c
#include <stdio.h>

int main() {
    // Creating a vector
    int numbers[3] = {1, 2, 3};
    
    // Multiplying by 2
    for (int i = 0; i < 3; i++) {
        numbers[i] *= 2;
    }
    
    // Displaying the vector
    printf("Multiplied vector: ");
    for (int i = 0; i < 3; i++) {
        printf("%d ", numbers[i]);
    }
    printf("\n");
    
    return 0;
}
```

### Explanation
- `int numbers[3] = {1, 2, 3};`: Creates a vector.
- `numbers[i] *= 2;`: Multiplies each element by 2.
- `for`: Displays the updated vector.

### Logic
Modifies all elements in the vector. Useful for adjusting values, like increasing prices.

### Output
```
Multiplied vector: 2 4 6
```

---

## SEVENTEENTH EXAMPLE: TRANSPOSING A MATRIX

```c
#include <stdio.h>

int main() {
    // Creating a 2x3 matrix
    int matrix[2][3] = {{1, 2, 3}, {4, 5, 6}};
    int transpose[3][2];
    
    // Calculating the transpose
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 2; j++) {
            transpose[i][j] = matrix[j][i];
        }
    }
    
    // Displaying the transpose
    printf("Transposed matrix:\n");
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 2; j++) {
            printf("%d ", transpose[i][j]);
        }
        printf("\n");
    }
    
    return 0;
}
```

### Explanation
- `int matrix[2][3]`: Creates a 2x3 matrix.
- `int transpose[3][2]`: Creates a 3x2 matrix for the transpose.
- `transpose[i][j] = matrix[j][i]`: Swaps rows and columns.
- `for`: Displays the transposed matrix.

### Logic
The transpose switches rows and columns. Useful in math and data science.

### Output
```
Transposed matrix:
1 4
2 5
3 6
```

---

## EIGHTEENTH EXAMPLE: SUMMING TWO MATRICES

```c
#include <stdio.h>

int main() {
    // Creating two 2x2 matrices
    int matrix1[2][2] = {{1, 2}, {3, 4}};
    int matrix2[2][2] = {{5, 6}, {7, 8}};
    int sum[2][2];
    
    // Summing
    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 2; j++) {
            sum[i][j] = matrix1[i][j] + matrix2[i][j];
        }
    }
    
    // Displaying the sum
    printf("Sum of matrices:\n");
    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 2; j++) {
            printf("%d ", sum[i][j]);
        }
        printf("\n");
    }
    
    return 0;
}
```

### Explanation
- `int matrix1[2][2], matrix2[2][2]`: Creates two 2x2 matrices.
- `int sum[2][2]`: Creates a matrix for the result.
- `sum[i][j] = matrix1[i][j] + matrix2[i][j]`: Adds corresponding elements.
- `for`: Displays the resulting matrix.

### Logic
Sums two matrices. Useful for combining data tables.

### Output
```
Sum of matrices:
6 8
10 12
```

---

## NINETEENTH EXAMPLE: CHECKING IF A MATRIX IS SQUARE

```c
#include <stdio.h>

int main() {
    // Creating a 3x3 matrix
    int matrix[3][3] = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
    
    // Checking if square
    int rows = 3;
    int columns = 3;
    if (rows == columns) {
        printf("The matrix is square!\n");
    } else {
        printf("The matrix is not square.\n");
    }
    
    return 0;
}
```

### Explanation
- `int matrix[3][3]`: Creates a 3x3 matrix.
- `int rows = 3; int columns = 3;`: Defines the number of rows and columns.
- `if`: Checks if rows equal columns.

### Logic
A square matrix has the same number of rows and columns. Useful in linear algebra.

### Output
```
The matrix is square!
```

---

## TWENTIETH EXAMPLE: CREATING AN IDENTITY MATRIX

```c
#include <stdio.h>

int main() {
    // Creating a 3x3 matrix
    int matrix[3][3];
    
    // Filling as identity
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            if (i == j) {
                matrix[i][j] = 1;
            } else {
                matrix[i][j] = 0;
            }
        }
    }
    
    // Displaying the matrix
    printf("Identity matrix:\n");
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }
    
    return 0;
}
```

### Explanation
- `int matrix[3][3];`: Creates a 3x3 matrix.
- `if (i == j)`: Sets 1 on the diagonal (where row = column).
- `else`: Sets 0 elsewhere.
- `for`: Displays the matrix.

### Logic
Creates an identity matrix (1s on the diagonal, 0s elsewhere). Used in math for neutral transformations.

### Output
```
Identity matrix:
1 0 0
0 1 0
0 0 1
```

---

## Tips for Learning

1. **Copy Carefully**: Write each line and read the comments to understand its purpose.
2. **Test the Code**: Use a C compiler (e.g., GCC, Dev-C++, OnlineGDB) to run and verify results.
3. **Modify the Code**: Change values, sizes, or messages to see how the program behaves.
4. **Take Notes**: Write down what each example teaches (e.g., "Example 6: looping through a vector").

If you need more examples or further explanations, let me know!