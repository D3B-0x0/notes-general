

# Sorting

1. Bubble sort
```c
#include <stdio.h>

void bubbleSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap arr[j] and arr[j + 1]
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}

int main() {
    int n;
    printf("Enter the number of elements: ");
    scanf("%d", &n);
    
    int arr[n];
    printf("Enter %d elements: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    bubbleSort(arr, n);
    
    printf("Sorted array: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    
    return 0;
}
```
![image](https://github.com/user-attachments/assets/3c8b6e78-9d6b-41c2-b803-dc774ea91f18)


2. Insertion sort

```c
#include <stdio.h>

void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;

        // Move elements of arr[0..i-1] that are greater than key
        // to one position ahead of their current position
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}

int main() {
    int n;
    printf("Enter the number of elements: ");
    scanf("%d", &n);
    
    int arr[n];
    printf("Enter %d elements: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    insertionSort(arr, n);
    
    printf("Sorted array: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    
    return 0;
}
```
![image](https://github.com/user-attachments/assets/46a0b9cc-6b00-489d-9059-5ec64668a5d3)


3. Merge sort

```c
#include <stdio.h>

void merge(int arr[], int left, int mid, int right) {
    int n1 = mid - left + 1;
    int n2 = right - mid;

    int L[n1], R[n2];

    for (int i = 0; i < n1; i++)
        L[i] = arr[left + i];
    for (int j = 0; j < n2; j++)
        R[j] = arr[mid + 1 + j];

    int i = 0, j = 0, k = left;
    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) {
            arr[k] = L[i];
            i++;
        } else {
            arr[k] = R[j];
            j++;
        }
        k++;
    }

    while (i < n1) {
        arr[k] = L[i];
        i++;
        k++;
    }

    while (j < n2) {
        arr[k] = R[j];
        j++;
        k++;
    }
}

void mergeSort(int arr[], int left, int right) {
    if (left < right) {
        int mid = left + (right - left) / 2;

        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);
        merge(arr, left, mid, right);
    }
}

int main() {
    int n;
    printf("Enter the number of elements: ");
    scanf("%d", &n);
    
    int arr[n];
    printf("Enter %d elements: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    mergeSort(arr, 0, n - 1);
    
    printf("Sorted array: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    
    return 0;
}
```
![image](https://github.com/user-attachments/assets/b2b4c0da-5bfe-4051-a0a4-220683fd82fe)


4. Quicksort
```c
#include <stdio.h>

int partition(int arr[], int low, int high) {
    int pivot = arr[high]; // Choosing the last element as pivot
    int i = (low - 1); // Index of smaller element

    for (int j = low; j < high; j++) {
        if (arr[j] < pivot) {
            i++;
            // Swap arr[i] and arr[j]
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
        }
    }
    // Swap arr[i + 1] and arr[high] (or pivot)
    int temp = arr[i + 1];
    arr[i + 1] = arr[high];
    arr[high] = temp;

    return i + 1;
}

void quickSort(int arr[], int low, int high) {
    if (low < high) {
        int pi = partition(arr, low, high);

        quickSort(arr, low, pi - 1);  // Before pi
        quickSort(arr, pi + 1, high); // After pi
    }
}

int main() {
    int n;
    printf("Enter the number of elements: ");
    scanf("%d", &n);
    
    int arr[n];
    printf("Enter %d elements: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    quickSort(arr, 0, n - 1);
    
    printf("Sorted array: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    
    return 0;
}
```
![image](https://github.com/user-attachments/assets/49e75158-9c01-4ca4-bf56-c5d570d44b7d)


5. Selection sort

```c
#include <stdio.h>

void selectionSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        int minIndex = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j; // Update minIndex if a smaller element is found
            }
        }
        // Swap the found minimum element with the first element
        if (minIndex != i) {
            int temp = arr[i];
            arr[i] = arr[minIndex];
            arr[minIndex] = temp;
        }
    }
}

int main() {
    int n;
    printf("Enter the number of elements: ");
    scanf("%d", &n);
    
    int arr[n];
    printf("Enter %d elements: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    selectionSort(arr, n);
    
    printf("Sorted array: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    
    return 0;
}
```
![image](https://github.com/user-attachments/assets/ff1565fe-8649-4b66-8876-53f1ceeb249f)


# Stack and queues

1. Circular queue 

```c
#include <stdio.h>
#define MAX 5

int queue[MAX];
int front = -1, rear = -1;

int isFull() {
    return ((rear + 1) % MAX == front);
}

int isEmpty() {
    return (front == -1);
}

void enqueue(int value) {
    if (isFull()) {
        printf("Queue is full\n");
        return;
    }
    if (isEmpty()) {
        front = 0;
    }
    rear = (rear + 1) % MAX;
    queue[rear] = value;
    printf("%d enqueued\n", value);
}

void dequeue() {
    if (isEmpty()) {
        printf("Queue is empty\n");
        return;
    }
    printf("%d dequeued\n", queue[front]);
    if (front == rear) {
        front = rear = -1; // Queue becomes empty
    } else {
        front = (front + 1) % MAX;
    }
}

void display() {
    if (isEmpty()) {
        printf("Queue is empty\n");
        return;
    }
    printf("Queue elements: ");
    int i = front;
    while (1) {
        printf("%d ", queue[i]);
        if (i == rear)
            break;
        i = (i + 1) % MAX;
    }
    printf("\n");
}

int main() {
    int choice, value;
    while (1) {
        printf("\n1.Enqueue\n2.Dequeue\n3.Display\n4.Exit\nChoose an option: ");
        scanf("%d", &choice);
        switch (choice) {
            case 1:
                printf("Enter value to enqueue: ");
                scanf("%d", &value);
                enqueue(value);
                break;
            case 2:
                dequeue();
                break;
            case 3:
                display();
                break;
            case 4:
                return 0;
            default:
                printf("Invalid choice\n");
        }
    }
}
```
![image](https://github.com/user-attachments/assets/a4d467a3-7c02-4e5a-a0fa-5d3ce8947924)


2. Queue using array

```c
#include <stdio.h>
#include <stdlib.h>
#define MAX 5

int queue[MAX], front = -1, rear = -1;

void enqueue(int item) {
    if (rear >= MAX - 1) {
        printf("Queue Overflow\n");
        return;
    }
    if (front == -1) front = 0;
    queue[++rear] = item;
    printf("%d enqueued\n", item);
}

int dequeue() {
    if (front == -1 || front > rear) {
        printf("Queue Underflow\n");
        return -1;
    }
    return queue[front++];
}

void display() {
    if (front == -1 || front > rear) {
        printf("Queue is empty\n");
        return;
    }
    printf("Queue: ");
    for (int i = front; i <= rear; i++)
        printf("%d ", queue[i]);
    printf("\n");
}

int main() {
    int choice, item;
    while (1) {
        printf("\n1. Enqueue\n2. Dequeue\n3. Display\n4. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        switch (choice) {
            case 1:
                printf("Enter item to enqueue: ");
                scanf("%d", &item);
                enqueue(item);
                break;
            case 2:
                item = dequeue();
                if (item != -1)
                    printf("%d dequeued\n", item);
                break;
            case 3:
                display();
                break;
            case 4:
                exit(0);
            default:
                printf("Invalid choice\n");
        }
    }
    return 0;
}
```
![image](https://github.com/user-attachments/assets/5d33db3e-ba07-4ac0-a0ae-5496d2ed8cb2)


3. Stack using array

```c
#include <stdio.h>
#include <stdlib.h>
#define MAX 5

int stack[MAX], top = -1;

void push(int item) {
    if (top >= MAX - 1) {
        printf("Stack Overflow\n");
        return;
    }
    stack[++top] = item;
    printf("%d pushed\n", item);
}

int pop() {
    if (top < 0) {
        printf("Stack Underflow\n");
        return -1;
    }
    return stack[top--];
}

void display() {
    if (top < 0) {
        printf("Stack is empty\n");
        return;
    }
    printf("Stack: ");
    for (int i = 0; i <= top; i++)
        printf("%d ", stack[i]);
    printf("\n");
}

int main() {
    int choice, item;
    while (1) {
        printf("\n1. Push\n2. Pop\n3. Display\n4. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        switch (choice) {
            case 1:
                printf("Enter item to push: ");
                scanf("%d", &item);
                push(item);
                break;
            case 2:
                item = pop();
                if (item != -1)
                    printf("%d popped\n", item);
                break;
            case 3:
                display();
                break;
            case 4:
                exit(0);
            default:
                printf("Invalid choice\n");
        }
    }
    return 0;
}
```
![image](https://github.com/user-attachments/assets/51ce9c24-e4ab-4a76-85e6-9f1ac1554e73)


4. Stack using linklist.

```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

struct Node* top = NULL;

void push(int item) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    if (!newNode) {
        printf("Memory allocation failed\n");
        return;
    }
    newNode->data = item;
    newNode->next = top;
    top = newNode;
    printf("%d pushed\n", item);
}

int pop() {
    if (!top) {
        printf("Stack Underflow\n");
        return -1;
    }
    struct Node* temp = top;
    int item = temp->data;
    top = top->next;
    free(temp);
    return item;
}

void display() {
    if (!top) {
        printf("Stack is empty\n");
        return;
    }
    printf("Stack: ");
    struct Node* current = top;
    while (current) {
        printf("%d ", current->data);
        current = current->next;
    }
    printf("\n");
}

int main() {
    int choice, item;
    while (1) {
        printf("\n1. Push\n2. Pop\n3. Display\n4. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        switch (choice) {
            case 1:
                printf("Enter item to push: ");
                scanf("%d", &item);
                push(item);
                break;
            case 2:
                item = pop();
                if (item != -1)
                    printf("%d popped\n", item);
                break;
            case 3:
                display();
                break;
            case 4:
                while (top) {
                    struct Node* temp = top;
                    top = top->next;
                    free(temp);
                }
                exit(0);
            default:
                printf("Invalid choice\n");
        }
    }
    return 0;
}
```
![image](https://github.com/user-attachments/assets/6577c9e6-4033-490d-be57-c04155a55dde)


5. Queue using linklist.

```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

struct Node* front = NULL;
struct Node* rear = NULL;

void enqueue(int item) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    if (!newNode) {
        printf("Memory allocation failed\n");
        return;
    }
    newNode->data = item;
    newNode->next = NULL;
    if (rear == NULL) {
        front = rear = newNode;
    } else {
        rear->next = newNode;
        rear = newNode;
    }
    printf("%d enqueued\n", item);
}

int dequeue() {
    if (front == NULL) {
        printf("Queue Underflow\n");
        return -1;
    }
    struct Node* temp = front;
    int item = temp->data;
    front = front->next;
    if (front == NULL) rear = NULL;
    free(temp);
    return item;
}

void display() {
    if (front == NULL) {
        printf("Queue is empty\n");
        return;
    }
    printf("Queue: ");
    struct Node* current = front;
    while (current) {
        printf("%d ", current->data);
        current = current->next;
    }
    printf("\n");
}

int main() {
    int choice, item;
    while (1) {
        printf("\n1. Enqueue\n2. Dequeue\n3. Display\n4. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        switch (choice) {
            case 1:
                printf("Enter item to enqueue: ");
                scanf("%d", &item);
                enqueue(item);
                break;
            case 2:
                item = dequeue();
                if (item != -1)
                    printf("%d dequeued\n", item);
                break;
            case 3:
                display();
                break;
            case 4:
                while (front) {
                    struct Node* temp = front;
                    front = front->next;
                    free(temp);
                }
                exit(0);
            default:
                printf("Invalid choice\n");
        }
    }
    return 0;
}
```
![image](https://github.com/user-attachments/assets/34ce5b05-6b7b-4749-8a2f-2495f99d565c)


# Searching

1. Linear search

```c
#include <stdio.h>
#include <stdlib.h>
#define MAX 5

int arr[MAX];

void input_array() {
    printf("Enter %d elements:\n", MAX);
    for (int i = 0; i < MAX; i++)
        scanf("%d", &arr[i]);
}

int linear_search(int key) {
    for (int i = 0; i < MAX; i++)
        if (arr[i] == key)
            return i;
    return -1;
}

void display() {
    printf("Array: ");
    for (int i = 0; i < MAX; i++)
        printf("%d ", arr[i]);
    printf("\n");
}

int main() {
    int choice, key, result;
    while (1) {
        printf("\n1. Input Array\n2. Linear Search\n3. Display\n4. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        switch (choice) {
            case 1:
                input_array();
                break;
            case 2:
                printf("Enter key to search: ");
                scanf("%d", &key);
                result = linear_search(key);
                if (result != -1)
                    printf("%d found at index %d\n", key, result);
                else
                    printf("%d not found\n", key);
                break;
            case 3:
                display();
                break;
            case 4:
                exit(0);
            default:
                printf("Invalid choice\n");
        }
    }
    return 0;
}
```
![image](https://github.com/user-attachments/assets/b4bd5586-7429-40c3-914d-3c70839e26c2)


2. Binary Search.

```c
#include <stdio.h>
#include <stdlib.h>
#define MAX 5

int arr[MAX];

void input_array() {
    printf("Enter %d elements in sorted order:\n", MAX);
    for (int i = 0; i < MAX; i++)
        scanf("%d", &arr[i]);
}

int binary_search(int key) {
    int left = 0, right = MAX - 1;
    while (left <= right) {
        int mid = (left + right) / 2;
        if (arr[mid] == key)
            return mid;
        if (arr[mid] < key)
            left = mid + 1;
        else
            right = mid - 1;
    }
    return -1;
}

void display() {
    printf("Array: ");
    for (int i = 0; i < MAX; i++)
        printf("%d ", arr[i]);
    printf("\n");
}

int main() {
    int choice, key, result;
    while (1) {
        printf("\n1. Input Array\n2. Binary Search\n3. Display\n4. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        switch (choice) {
            case 1:
                input_array();
                break;
            case 2:
                printf("Enter key to search: ");
                scanf("%d", &key);
                result = binary_search(key);
                if (result != -1)
                    printf("%d found at index %d\n", key, result);
                else
                    printf("%d not found\n", key);
                break;
            case 3:
                display();
                break;
            case 4:
                exit(0);
            default:
                printf("Invalid choice\n");
        }
    }
    return 0;
}
```
![image](https://github.com/user-attachments/assets/d3bfd6f5-5567-4af0-854d-41eed8b7215c)


# Linkedlist

1. Circular linkedlist.
```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

struct Node* last = NULL;

void insert(int item) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    if (!newNode) {
        printf("Memory allocation failed\n");
        return;
    }
    newNode->data = item;
    if (last == NULL) {
        last = newNode;
        last->next = last;
    } else {
        newNode->next = last->next;
        last->next = newNode;
        last = newNode;
    }
    printf("%d inserted\n", item);
}

void delete(int key) {
    if (last == NULL) {
        printf("List is empty\n");
        return;
    }
    struct Node *current = last->next, *prev = last;
    int found = 0;
    do {
        if (current->data == key) {
            found = 1;
            if (current == last && current->next == current) {
                last = NULL;
            } else {
                prev->next = current->next;
                if (current == last) last = prev;
            }
            free(current);
            printf("%d deleted\n", key);
            break;
        }
        prev = current;
        current = current->next;
    } while (current != last->next);
    if (!found) printf("%d not found\n", key);
}

void display() {
    if (last == NULL) {
        printf("List is empty\n");
        return;
    }
    printf("List: ");
    struct Node* current = last->next;
    do {
        printf("%d ", current->data);
        current = current->next;
    } while (current != last->next);
    printf("\n");
}

int main() {
    int choice, item;
    while (1) {
        printf("\n1. Insert\n2. Delete\n3. Display\n4. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        switch (choice) {
            case 1:
                printf("Enter item to insert: ");
                scanf("%d", &item);
                insert(item);
                break;
            case 2:
                printf("Enter item to delete: ");
                scanf("%d", &item);
                delete(item);
                break;
            case 3:
                display();
                break;
            case 4:
                while (last != NULL) {
                    struct Node* temp = last->next;
                    last->next = temp->next;
                    free(temp);
                    if (last->next == last) {
                        free(last);
                        last = NULL;
                    }
                }
                exit(0);
            default:
                printf("Invalid choice\n");
        }
    }
    return 0;
}
```
![image](https://github.com/user-attachments/assets/70fef3d3-eb0f-4f65-b9de-53ffbd920428)


2. Doubly linkedlist.

```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* prev;
    struct Node* next;
};

struct Node* head = NULL;

void insert(int item) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    if (!newNode) {
        printf("Memory allocation failed\n");
        return;
    }
    newNode->data = item;
    newNode->prev = NULL;
    newNode->next = head;
    if (head != NULL) head->prev = newNode;
    head = newNode;
    printf("%d inserted\n", item);
}

void delete(int key) {
    struct Node* current = head;
    if (current == NULL) {
        printf("List is empty\n");
        return;
    }
    while (current != NULL && current->data != key) {
        current = current->next;
    }
    if (current == NULL) {
        printf("%d not found\n", key);
        return;
    }
    if (current->prev != NULL) current->prev->next = current->next;
    else head = current->next;
    if (current->next != NULL) current->next->prev = current->prev;
    free(current);
    printf("%d deleted\n", key);
}

void display() {
    if (head == NULL) {
        printf("List is empty\n");
        return;
    }
    printf("List: ");
    struct Node* current = head;
    while (current != NULL) {
        printf("%d ", current->data);
        current = current->next;
    }
    printf("\n");
}

int main() {
    int choice, item;
    while (1) {
        printf("\n1. Insert\n2. Delete\n3. Display\n4. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        switch (choice) {
            case 1:
                printf("Enter item to insert: ");
                scanf("%d", &item);
                insert(item);
                break;
            case 2:
                printf("Enter item to delete: ");
                scanf("%d", &item);
                delete(item);
                break;
            case 3:
                display();
                break;
            case 4:
                while (head != NULL) {
                    struct Node* temp = head;
                    head = head->next;
                    free(temp);
                }
                exit(0);
            default:
                printf("Invalid choice\n");
        }
    }
    return 0;
}
```
![image](https://github.com/user-attachments/assets/43d4fdb4-17bb-4395-9054-43e5e518265c)


3. Singly linkedlist.

```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

struct Node* head = NULL;

void insert(int item) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    if (!newNode) {
        printf("Memory allocation failed\n");
        return;
    }
    newNode->data = item;
    newNode->next = head;
    head = newNode;
    printf("%d inserted\n", item);
}

void delete(int key) {
    struct Node *current = head, *prev = NULL;
    if (current == NULL) {
        printf("List is empty\n");
        return;
    }
    while (current != NULL && current->data != key) {
        prev = current;
        current = current->next;
    }
    if (current == NULL) {
        printf("%d not found\n", key);
        return;
    }
    if (prev == NULL) head = current->next;
    else prev->next = current->next;
    free(current);
    printf("%d deleted\n", key);
}

void display() {
    if (head == NULL) {
        printf("List is empty\n");
        return;
    }
    printf("List: ");
    struct Node* current = head;
    while (current != NULL) {
        printf("%d ", current->data);
        current = current->next;
    }
    printf("\n");
}

int main() {
    int choice, item;
    while (1) {
        printf("\n1. Insert\n2. Delete\n3. Display\n4. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        switch (choice) {
            case 1:
                printf("Enter item to insert: ");
                scanf("%d", &item);
                insert(item);
                break;
            case 2:
                printf("Enter item to delete: ");
                scanf("%d", &item);
                delete(item);
                break;
            case 3:
                display();
                break;
            case 4:
                while (head != NULL) {
                    struct Node* temp = head;
                    head = head->next;
                    free(temp);
                }
                exit(0);
            default:
                printf("Invalid choice\n");
        }
    }
    return 0;
}
```
![image](https://github.com/user-attachments/assets/ecf2768c-59dc-45f3-809c-7616bef882b1)


4. Polynomial addition using a singly linked list.
```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int coeff;
    int exp;
    struct Node* next;
};

struct Node *poly1 = NULL, *poly2 = NULL, *result = NULL;

void insert(struct Node** poly, int coeff, int exp) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    if (!newNode) {
        printf("Memory allocation failed\n");
        return;
    }
    newNode->coeff = coeff;
    newNode->exp = exp;
    newNode->next = *poly;
    *poly = newNode;
}

void input_poly(struct Node** poly) {
    int n, coeff, exp;
    printf("Enter number of terms: ");
    scanf("%d", &n);
    for (int i = 0; i < n; i++) {
        printf("Enter coefficient and exponent: ");
        scanf("%d %d", &coeff, &exp);
        insert(poly, coeff, exp);
    }
}

void add_polynomials() {
    struct Node *p1 = poly1, *p2 = poly2;
    result = NULL;
    while (p1 && p2) {
        struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
        if (!newNode) {
            printf("Memory allocation failed\n");
            return;
        }
        if (p1->exp > p2->exp) {
            newNode->coeff = p1->coeff;
            newNode->exp = p1->exp;
            p1 = p1->next;
        } else if (p1->exp < p2->exp) {
            newNode->coeff = p2->coeff;
            newNode->exp = p2->exp;
            p2 = p2->next;
        } else {
            newNode->coeff = p1->coeff + p2->coeff;
            newNode->exp = p1->exp;
            p1 = p1->next;
            p2 = p2->next;
        }
        if (newNode->coeff != 0) {
            newNode->next = result;
            result = newNode;
        } else {
            free(newNode);
        }
    }
    while (p1) {
        insert(&result, p1->coeff, p1->exp);
        p1 = p1->next;
    }
    while (p2) {
        insert(&result, p2->coeff, p2->exp);
        p2 = p2->next;
    }
}

void display(struct Node* poly) {
    if (!poly) {
        printf("Polynomial is empty\n");
        return;
    }
    printf("Polynomial: ");
    struct Node* current = poly;
    while (current) {
        printf("%dx^%d", current->coeff, current->exp);
        current = current->next;
        if (current) printf(" + ");
    }
    printf("\n");
}

int main() {
    int choice;
    while (1) {
        printf("\n1. Input Polynomial 1\n2. Input Polynomial 2\n3. Add Polynomials\n4. Display Result\n5. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        switch (choice) {
            case 1:
                input_poly(&poly1);
                break;
            case 2:
                input_poly(&poly2);
                break;
            case 3:
                add_polynomials();
                printf("Polynomials added\n");
                break;
            case 4:
                display(result);
                break;
            case 5:
                while (poly1) {
                    struct Node* temp = poly1;
                    poly1 = poly1->next;
                    free(temp);
                }
                while (poly2) {
                    struct Node* temp = poly2;
                    poly2 = poly2->next; 
                    free(temp);
                }
                while (result) {
                    struct Node* temp = result;
                    result = result->next;
                    free(temp);
                }
                exit(0);
            default:
                printf("Invalid choice\n");
        }
    }
    return 0;
}
```
![image](https://github.com/user-attachments/assets/e79c98a9-a9a5-483a-a4bc-499e00924e47)


# Tree

1. Binary search tree.

```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *left, *right;
};

struct Node* insert(struct Node* root, int x) {
    if (!root) {
        root = malloc(sizeof(struct Node));
        root->data = x;
        root->left = root->right = NULL;
    }
    else if (x < root->data) root->left = insert(root->left, x);
    else if (x > root->data) root->right = insert(root->right, x);
    return root;
}

struct Node* search(struct Node* root, int x) {
    if (!root || root->data == x) return root;
    return (x < root->data) ? search(root->left, x) : search(root->right, x);
}

void inorder(struct Node* root) {
    if (root) {
        inorder(root->left);
        printf("%d ", root->data);
        inorder(root->right);
    }
}

int main() {
    struct Node* root = NULL;
    int choice, x;
    
    while (1) {
        printf("\n1.Insert 2.Search 3.Display 4.Exit\nChoice: ");
        scanf("%d", &choice);
        
        if (choice == 1) {
            printf("Value: ");
            scanf("%d", &x);
            root = insert(root, x);
        }
        else if (choice == 2) {
            printf("Search: ");
            scanf("%d", &x);
            printf(search(root, x) ? "Found\n" : "Not found\n");
        }
        else if (choice == 3) {
            printf("Tree: ");
            inorder(root);
            printf("\n");
        }
        else break;
    }
    return 0;
}
```
![image](https://github.com/user-attachments/assets/49bd1092-7d71-47db-b588-d75f8b068982)


#ENDDDDDDDDDD
---

