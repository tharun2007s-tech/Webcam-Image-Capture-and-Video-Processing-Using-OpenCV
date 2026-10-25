# Image Capture and Video Processing Using OpenCV

---

## Aim

To write a Python program using OpenCV to capture an image from the webcam and perform the following operations:

1. Write the frame as a JPG file  
2. Display the video  
3. Display the video by resizing the window  
4. Rotate and display the video  

---

## 🛠️ Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  

---

## ⚙️ Algorithm

### Step 1:
Import the required libraries and initialize the webcam using `cv2.VideoCapture()`.

### Step 2:
Capture frames continuously from the webcam.

### Step 3:
Save a frame as a JPG image using `cv2.imwrite()`.

### Step 4:
Display the live video stream using `cv2.imshow()`.

### Step 5:
Resize the frame and rotate it using OpenCV functions, then display the processed frames.

---

## 💻 Program

# Step 1: Import the required libraries and initialize the webcam using cv2.VideoCapture()[cite: 1]
```
import cv2
def main():
    cap = cv2.VideoCapture(0)
    
    if not cap.isOpened():
        print("Error: Could not open webcam.")
        return

    image_saved = False
```

 # Step 2: Capture frames continuously from the webcam[cite: 1]
```
while True:
    ret, frame = cap.read()
if not ret:
    print("Error: Failed to grab frame.")
    break
```
  # Step 3: Save a frame as a JPG image using cv2.imwrite()[cite: 1]
  ```
  if not image_saved:
    cv2.imwrite('captured_frame.jpg', frame)
    print("Saved initial frame as 'captured_frame.jpg'.")
    image_saved = True
```
        
# Step 4: Display the live video stream using cv2.imshow()[cite: 1]
```
cv2.imshow('Live Video Stream', frame)
```

# Step 5: Resize the frame and rotate it using OpenCV functions, then display the processed frames[cite: 1]
# Resize the frame to 50% scale
```
resized_frame = cv2.resize(frame, (0, 0), fx=0.5, fy=0.5)
```
# Rotate the frame by 90 degrees around its center
```
height, width = frame.shape[:2]
center = (width / 2, height / 2)
rot_matrix = cv2.getRotationMatrix2D(center, angle=90, scale=1.0)
rotated_frame = cv2.warpAffine(frame, rot_matrix, (width, height))
```
# Display the processed frames
```
cv2.imshow('Resized Frame', resized_frame)
cv2.imshow('Rotated Frame', rotated_frame)
```
# Press the 'q' key on your keyboard to exit the loop
```
if cv2.waitKey(1) & 0xFF == ord('q'):
    break
```
# Release the webcam and close all OpenCV windows
```
cap.release()
cv2.destroyAllWindows()
```
```
if __name__ == "__main__":
    main()
```

### Developed By:
**Name:** Tharun S

### Register No:
212225240174

---

## Output

### i) Write the frame as JPG image
Captured image is saved as `captured_image.jpg`

### ii) Display the video
Live webcam video is displayed

### iii) Display the video by resizing the window
Video is shown in resized resolution (640 × 480)

### iv) Rotate and display the video
Video is displayed after rotation (90° clockwise)

<img width="1920" height="977" alt="Screenshot 2026-10-25 160754" src="https://github.com/user-attachments/assets/93d288f9-93c5-4f1a-9ee5-3a0b129dd29d" />


---

## Result

Thus, the image is successfully captured from the webcam and various video processing operations such as saving, displaying, resizing, and rotating are performed using OpenCV.
