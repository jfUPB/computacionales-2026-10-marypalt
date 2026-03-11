# Unidad 4

## Bitácora de proceso de aprendizaje


## Bitácora de aplicación 
ffApp.h:
```
#pragma once
#include "ofMain.h"

// Nodo de la cola
struct Node {
    float x, y;
    float radius;
    ofColor color;
    float opacity;
    Node* next;

    Node(float _x, float _y, float _radius, ofColor _color, float _opacity)
        : x(_x), y(_y), radius(_radius), color(_color), opacity(_opacity), next(nullptr) {
    }
};

// Implementación manual de una cola (FIFO)
class BrushQueue {
public:
    Node* front;
    Node* rear;
    int size;
    int maxSize;

    BrushQueue(int _maxSize);
    ~BrushQueue();

    void enqueue(float x, float y, float radius, ofColor color, float opacity);
    void dequeue();
    void clear();
    bool isEmpty();
};


// Constructor
BrushQueue::BrushQueue(int _maxSize) : front(nullptr), rear(nullptr), size(0), maxSize(_maxSize) {}

// Destructor
BrushQueue::~BrushQueue() {
    clear();
}

//--------------------------------------------------------------
// ENQUEUE
//--------------------------------------------------------------
void BrushQueue::enqueue(float x, float y, float radius, ofColor color, float opacity) {

    Node* newNode = new Node(x, y, radius, color, opacity);

    if (isEmpty()) {
        front = newNode;
        rear = newNode;
    }
    else {
        rear->next = newNode;
        rear = newNode;
    }

    size++;

    if (size > maxSize) {
        dequeue();
    }
}

//--------------------------------------------------------------
// DEQUEUE
//--------------------------------------------------------------
void BrushQueue::dequeue() {

    if (isEmpty()) return;

    Node* temp = front;
    front = front->next;

    delete temp;

    size--;

    if (front == nullptr) {
        rear = nullptr;
    }
}

//--------------------------------------------------------------
// CLEAR
//--------------------------------------------------------------
void BrushQueue::clear() {

    while (!isEmpty()) {
        dequeue();
    }
}

//--------------------------------------------------------------
// ISEMPTY
//--------------------------------------------------------------
bool BrushQueue::isEmpty() {

    return front == nullptr;
}


//--------------------------------------------------------------
// OF APP
//--------------------------------------------------------------
class ofApp : public ofBaseApp {
public:
    BrushQueue strokes; // Cola de trazos
    float backgroundHue = 0;

    ofApp() : strokes(50) {} // Tamaño máximo de la cola

    void setup();
    void update();
    void draw();
    void keyPressed(int key);
};
```
ofApp.cpp:
```
#include "ofApp.h"

//--------------------------------------------------------------
void ofApp::setup() {
    ofBackground(0);
}

//--------------------------------------------------------------
void ofApp::update() {

    backgroundHue += 0.2;
    if (backgroundHue > 255) backgroundHue = 0;

    // Agregar trazo si el mouse está presionado
    if (ofGetMousePressed()) {

        float x = ofGetMouseX();
        float y = ofGetMouseY();

        float radius = ofRandom(5, 20);

        ofColor color;
        color.setHsb(ofRandom(255), 200, 255);

        float opacity = 255;

        strokes.enqueue(x, y, radius, color, opacity);
    }
}

//--------------------------------------------------------------
void ofApp::draw() {

    // Fondo con gradiente dinámico
    ofColor color1, color2;
    color1.setHsb(backgroundHue, 150, 240);
    color2.setHsb(fmod(backgroundHue + 128, 255), 150, 240);
    ofBackgroundGradient(color1, color2, OF_GRADIENT_LINEAR);

    Node* current = strokes.front;

    int index = 0;

    while (current != nullptr) {

        float alpha = ofMap(index, 0, strokes.size, 50, 255);

        ofSetColor(current->color, alpha);

        ofDrawCircle(current->x, current->y, current->radius);

        current = current->next;

        index++;
    }
}

//--------------------------------------------------------------
void ofApp::keyPressed(int key) {

    if (key == 'c') {

        strokes.clear();
    }

    if (key == 'a') {

        if (strokes.maxSize == 50)
            strokes.maxSize = 100;
        else
            strokes.maxSize = 50;
    }

    else if (key == 's') {

        ofSaveScreen("screenshot.png");
    }
}
```






## Bitácora de reflexión
