# ED1 — TAD Lista Sequencial (ArrayList)

Implementação de uma **Lista Sequencial (ArrayList)** em **C++** utilizando conceitos de **Tipo Abstrato de Dados (TAD)**, programação genérica (*templates*) e alocação dinâmica com capacidade fixa.

O projeto apresenta uma arquitetura modular estruturada em:
- **Interface Abstrata (`include/List.h`):** Define o contrato de métodos que qualquer implementação de lista deve seguir.
- **Implementação Concreta (`include/ArrayList.h`):** Implementa a lista sobre um vetor contíguo na memória, gerenciando capacidade, inserções, remoções e buscas.
- **Bateria de Testes (`src/ArrayListTest.cpp` / `main.cpp`):** Valida formalmente cada operação disponibilizada pelo TAD.

> **Instituto Federal do Triângulo Mineiro — Campus Patrocínio**  
> **Curso:** Tecnologia em Análise e Desenvolvimento de Sistemas — 3º Período  
> **Disciplina:** Estrutura de Dados I  
> **Professor:** Júnio Moreira  
> **Data:** 24/09/2026  
> **Aluno:** Jeferson Silva Lima  

---

## Estrutura do Diretório

ed1_list_cpp/
├── include/
│   ├── ArrayList.h
│   └── List.h
├── src/
│   └── ArrayListTest.cpp
├── CMakeLists.txt
├── main.cpp
├── .gitignore
└── README.md

---

## Funcionalidades Implementadas

| Operação | Método | Descrição | Complexidade |
| :--- | :--- | :--- | :---: |
| **Inserção no Início** | `addFirst(T el)` | Insere um elemento na posição 0 deslocando os demais. | O(n) |
| **Inserção no Fim** | `addLast(T el)` | Insere um elemento na última posição vaga. | O(1) |
| **Inserção em Posição** | `insertAt(int idx, T el)` | Insere um elemento em índice específico com deslocamento. | O(n) |
| **Inserção Ordenada** | `addSorted(T el)` | Insere mantendo a lista em ordem crescente. | O(n) |
| **Remoção no Início** | `removeFirst()` | Remove e retorna o primeiro elemento. | O(n) |
| **Remoção no Fim** | `removeLast()` | Remove e retorna o último elemento. | O(1) |
| **Remoção por Posição** | `removeAt(int idx)` | Remove e retorna o elemento na posição solicitada. | O(n) |
| **Remoção por Valor** | `remove(T el)` | Localiza o elemento e o remove da lista. | O(n) |
| **Busca por Posição** | `get(int idx)` | Acesso direto ao elemento pelo índice. | O(1) |
| **Busca por Elemento** | `find(T el)` | Retorna o índice do elemento ou -1 se ausente. | O(n) |
| **Alteração de Valor** | `set(int idx, T el)` | Substitui o valor contido no índice informado. | O(1) |
| **Representação em Texto** | `toString()` | Retorna a lista formatada (ex.: [1, 2, 3]). | O(n) |

---

## Requisitos de Ambiente

Para compilar e executar o projeto, certifique-se de possuir instalado:
- **Compilador C++** com suporte a **C++17** ou superior (`g++` / `clang++` / `MSVC`).
- **CMake** (versão 3.15 ou superior) ou **MinGW/g++** no terminal.

---

## Instruções de Compilação e Execução

### Opção 1: Compilando via Terminal com g++ (Recomendado)

Abra o terminal na pasta raiz do projeto (`ed1_list_cpp`) e execute:

#### Windows (PowerShell ou CMD):
g++ -std=c++17 -Wall main.cpp -I include -o main.exe
.\main.exe

#### Linux / macOS:
g++ -std=c++17 -Wall main.cpp -I include -o main
./main

---

### Opção 2: Compilando com CMake

1. Cria a pasta de compilação e acessa:
mkdir build
cd build

2. Gera os arquivos de compilação:
cmake ..

3. Compila o projeto:
cmake --build .

4. Executa:
# No Windows:
.\main.exe
# No Linux / macOS:
./main

---

### Opção 3: Executando via CLion ou VS Code

- **CLion:** Abra a pasta raiz contendo o `CMakeLists.txt`. A IDE detectará o projeto automaticamente; clique no botão **Run** (`Shift + F10`).
- **VS Code:** Abra a pasta raiz, certifique-se de possuir a extensão C/C++ ativa e utilize o comando de build ou execute via terminal integrado.

---

## Saída Esperada dos Testes

Ao rodar o programa, a saída dos testes no terminal deve ser:

--- [ArrayList] Initial Tests (addLast, size, find, and get) ---
Expected size (1): 1
Current list: [1]
Current list: [1, 2]
Current list: [1, 2, 3]
******* Search by element *******
Position of element 1 (expected 0): 0
Position of element 0 (expected -1): -1
******* Search by position *******
Element at pos 0 (expected 1): 1

--- [ArrayList] Test Add First (addFirst) ---
Expected list [1, 2, 3]: [1, 2, 3]

--- [ArrayList] Test Insert At Position (insertAt) ---
Expected list [0, 1, 2, 3, 4, 5]: [0, 1, 2, 3, 4, 5]

--- [ArrayList] Test Remove First (removeFirst) ---
Expected removed (1): 1
Expected remaining list [2, 3]: [2, 3]

--- [ArrayList] Test Remove Last (removeLast) ---
Expected removed (3): 3
Expected remaining list [1, 2]: [1, 2]

--- [ArrayList] Test Remove At Position (removeAt) ---
Element removed at pos 4 (expected 5): 5
Expected remaining list [1, 2, 3, 4]: [1, 2, 3, 4]

--- [ArrayList] Test Remove By Element (remove) ---
Removed 20? (true): true
Expected remaining list [10, 30]: [10, 30]
Trying to remove 99 again (false): false

--- [ArrayList] Test Element Modification (set) ---
List before set: [10, 20]
List after set (expected [10, 99]): [10, 99]

--- [ArrayList] Test Sorted Insertion (addSorted) ---
Expected auto-sorted list [5, 10, 20, 30]: [5, 10, 20, 30]

--- [ArrayList] Test Static Limit (Full List) ---
Trying to insert the third element into an array of capacity 2:
Error: List is full!
