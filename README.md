#include <stdio.h>
#include <stdlib.h>

struct Node {
  int data;
  struct Node next;
};

// Function to create a new node
struct Node createNode(int data) {
  struct Node newNode = (struct Node )malloc(sizeof(struct Node));
  newNode->data = data;
  newNode->next = NULL;
  return newNode;
}

// Function to insert a node at the beginning of the linked list
void insertAtBeginning(struct Node head, int data) {
  struct Node newNode = createNode(data);
  newNode->next = head;
  head = newNode;
}

// Function to insert a node at the end of the linked list
void insertAtEnd(struct Node head, int data) {
  struct Node newNode = createNode(data);
  if (head == NULL) {
    head = newNode;
    return;
  }
  struct Node temp = head;
  while (temp->next != NULL) {
    temp = temp->next;
  }
  temp->next = newNode;
}

// Function to print the linked list
void printLinkedList(struct Node head) {
  struct Node temp = head;
  while (temp != NULL) {
    printf("%d ", temp->data);
    temp = temp->next;
  }
}

// Function to delete a node from the linked list
void deleteNode(struct Node head, int data) {
  if (head == NULL) {
    return;
  }
  if ((head)->data == data) {
    head = (head)->next;
    return;
  }
  struct Node temp = head;
  struct Node prev = NULL;
  while (temp != NULL && temp->data != data) {
    prev = temp;
    temp = temp->next;
  }
  if (temp == NULL) {
    return;
  }
  prev->next = temp->next;
  free(temp);
}

int main() {
  struct Node head = NULL;
  insertAtBeginning(&head, 10);
  insertAtEnd(&head, 20);
  insertAtEnd(&head, 30);
  insertAtEnd(&head, 40);
  printLinkedList(head);
  printf("\n");
  deleteNode(&head, 20);
  printLinkedList(head);
  printf("\n");
  deleteNode(&head, 40);
  printLinkedList(head);
  printf("\n");
  return 0;
}
