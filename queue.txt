#include <iostream>
using namespace std;
#define MAX_SIZE 100 // maximum size of the queue

class Queue {
private:
    int arr[MAX_SIZE];
    int front;
    int rear;
    int size;

public:
    Queue() {
        front = 0;
        rear = -1;
        size = 0;
    }

    // Enqueue operation
    void enqueue(int value) {
        if (size == MAX_SIZE) {
            cout << "Queue overflow\n";
            return;
        }
        rear = (rear + 1) % MAX_SIZE;
        arr[rear] = value;
        size++;
    }

    // Dequeue operation
    int dequeue() {
        if (size == 0) {
            cout << "Queue underflow\n";
            return -1;
        }
        int result = arr[front];
        front = (front + 1) % MAX_SIZE;
        size--;
        return result;
    }

    // Check if the queue is empty
    bool isEmpty() {
        return size == 0;
    }

    // Check if the queue is full
    bool isFull() {
        return size == MAX_SIZE;
    }

    // Get the front item of the queue
    int getFront() {
        if (isEmpty()) {
            cout << "Queue is empty\n";
            return -1;
        }
        return arr[front];
    }

    // Get the rear item of the queue
    int getRear() {
        if (isEmpty()) {
            cout << "Queue is empty\n";
            return -1;
        }
        return arr[rear];
    }
};

int main() {
    int num1, num2, num3;

    cout << "Enter first number to add to queue\n";
    cin >> num1;
    cout << "Enter second number to add to queue\n";
    cin >> num2;
    cout << "Enter third number to add to queue\n";
    cin >> num3;


    Queue q;

    q.enqueue(num1);
    q.enqueue(num2);
    q.enqueue(num3);

    cout << "Dequeued: " << q.dequeue() << endl;
    cout << "Front: " << q.getFront() << endl; 
    cout << "Rear: " << q.getRear() << endl; 

    return 0;
}
