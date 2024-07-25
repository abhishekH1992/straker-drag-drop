# Drag & Drop Objects

## Table of Content
- [Overview](#overview)
- [Demo](#demo)
- [Technology](#technology)
- [Project Setup](#project-setup)
- [Explanation](#explanation)

## Overview
This is simple drag and drop object project and it sends a request to server once object dragging finish.

## Demo
[Online Demo](https://play.vuejs.org/#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)

## Technology
```Vue 3```

## Project Setup
### Clone Git Repository
```
git clone https://github.com/abhishekH1992/straker-drag-drop.git
```
### Install NPM Dependency
```
npm i
```
### Run project
```
npm run dev
```

## Explanation
#### Attach Event to div
Used mousedown event which triggers when a mouse button is pressed down on an element/object.
```
<div 
    ref="square"
    id="square"
    class="card"
    @mousedown="(e) => startDrag(e, square)"
></div>
<div 
    ref="circle"
    id="circle"
    class="card card-circle"
    @mousedown="(e) => startDrag(e, circle)"
></div>
```
#### startDrag function
This function takes two parameters event and element. Add class `absolute` to it and then call drag function
```
const startDrag = (e, element) => {
    currentElement = element;
    if (currentElement) {
        currentElement.classList.add('absolute');
    }
    drag(e);
};
```
#### drag function
This function capture the mouse position when dragging starts. It uses `getBoundingClientRect()` method which is built-in function on DOM element. It provides information about size of an element and it's position. Then it sets offset values of element. Once that is done it attach `mousemove` and `mouseup` events.
```
const drag = (e) => {
    startXCordinate = e.clientX;
    startYCordinate = e.clientY;
    if (currentElement) {
        const rect = currentElement.getBoundingClientRect();
        offsetLeft = rect.left;
        offsetTop = rect.top;
    }
    document.addEventListener('mousemove', dragOn);
    document.addEventListener('mouseup', dragOff);
};
```
#### dragOn function
It calculates the new position based on mouse movement and update the elemnet's position by adding in mouse coordinates
```
const dragOn = (e) => {
    if (currentElement) {
        const containerRect = currentElement.parentElement.getBoundingClientRect();
        const newLeft = e.clientX - containerRect.left - (currentElement.offsetWidth / 2);
        const newTop = e.clientY - containerRect.top - (currentElement.offsetHeight / 2);        
        currentElement.style.left = `${newLeft}px`;
        currentElement.style.top = `${newTop}px`;
    }
};
```
#### dragOff function
This functions get triggered when mouse movement is stopped. It removes the `mousemove` and `mouseup` events. Then it gets the value of coordinates and sends a request to backend using fetch.
```
const dragOff = () => {
    document.removeEventListener('mousemove', dragOn);
    document.removeEventListener('mouseup', dragOff);
    
    if (currentElement) {
        const left = currentElement.style.left;
        const top = currentElement.style.top;
        fetch('/api/drag-end', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
            },
            body: JSON.stringify({
                id: currentElement.id,
                left: left,
                top: top,
            }),
        })
        .then(response => response.json())
        .then(data => console.log('Drag position sent to backend:', data))
        .catch(error => console.error('Error sending drag position to backend:', error));
    }
    currentElement = null;
};
```