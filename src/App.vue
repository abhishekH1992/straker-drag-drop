<template>
    <div class="container">
        <!-- Draggable square element -->
        <div 
            ref="square"
            id="square"
            class="card"
            @mousedown="(e) => startDrag(e, square)"
        ></div>
    
        <!-- Draggable circle element -->
        <div 
            ref="circle"
            id="circle"
            class="card card-circle"
            @mousedown="(e) => startDrag(e, circle)"
        ></div>
    </div>
</template>
<script setup>
import { ref } from 'vue';
  
    // Reactive references to the draggable elements
    const square = ref(null);
    const circle = ref(null);
  
    // Variables to store the initial mouse position and element position
    let startXCordinate = 0;
    let startYCordinate = 0;
    let offsetLeft = 0;
    let offsetTop = 0;
    let currentElement = null; // Reference to the currently dragged element
  
    // Function to initialize dragging
    const drag = (e) => {
        // Capture the mouse position when dragging starts
        startXCordinate = e.clientX;
        startYCordinate = e.clientY;
    
        // Capture the current position of the element to calculate movement
        if (currentElement) {
            const rect = currentElement.getBoundingClientRect();
            offsetLeft = rect.left;
            offsetTop = rect.top;
        }
    
        // Add event listeners to update element position and handle drag end
        document.addEventListener('mousemove', dragOn);
        document.addEventListener('mouseup', dragOff);
    };
  
    // Function to update the position of the element while dragging
    const dragOn = (e) => {
        if (currentElement) {
            // Calculate the new position based on mouse movement
            // Update the element's position by adding the change in mouse coordinates
            const containerRect = currentElement.parentElement.getBoundingClientRect();
            const newLeft = e.clientX - containerRect.left - (currentElement.offsetWidth / 2);
            const newTop = e.clientY - containerRect.top - (currentElement.offsetHeight / 2);
        
            currentElement.style.left = `${newLeft}px`;
            currentElement.style.top = `${newTop}px`;
        }
    };
  
    // Function to finalize dragging and send the position data to the backend
    const dragOff = () => {
        // Remove event listeners to stop tracking mouse movement and drag end
        document.removeEventListener('mousemove', dragOn);
        document.removeEventListener('mouseup', dragOff);
    
        // Send the final position of the element to the backend
        if (currentElement) {
            const left = currentElement.style.left;
            const top = currentElement.style.top;
            // Uncomment and use the following code to send the position data to the backend
            /*
            fetch('/api/drag-end', {
                method: 'POST',
                headers: {
                'Content-Type': 'application/json',
                },
                body: JSON.stringify({
                id: currentElement.id, // Include the ID of the dragged element
                left: left,
                top: top,
                }),
            })
                .then(response => response.json())
                .then(data => console.log('Drag position sent to backend:', data))
                .catch(error => console.error('Error sending drag position to backend:', error));
            */
        }
  
        // Reset the current element after drag is complete
        currentElement = null;
    };
  
    // Function to start dragging for a specific element
    const startDrag = (e, element) => {
        currentElement = element;
        // Ensure the element has the absolute class for positioning
        if (currentElement) {
            currentElement.classList.add('absolute');
        }
        drag(e);
    };
  </script>
  
  <style scoped>
    .container {
        width: 100%;
        height: 100vh;
        position: relative; /* Ensure container is the positioning context */
    }
    
    .card {
        width: 100px;
        height: 100px;
        background-color: red;
        cursor: grab;
    }
    
    .card-circle {
        border-radius: 50%; /* Make the element circular */
        background-color: green;
    }
    
    .absolute {
        position: absolute; /* Ensure absolute positioning */
    }
  </style>
  