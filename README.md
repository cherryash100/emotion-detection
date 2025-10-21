Webcam Emotion Analyzer in Google Colab

This project is a simple, self-contained Google Colab notebook that uses your webcam to capture a single photo and then analyzes it with the **DeepFace** library to determine the dominant emotion.

## Key Features

  * **Runs Entirely in Colab:** No local Python environment or IDE setup is required.
  * **Webcam Integration:** Uses JavaScript within the Colab output to access your computer's webcam.
  * **State-of-the-Art Analysis:** Leverages the powerful `deepface` library to perform emotion recognition.
  * **Instant Feedback:** Captures an image and immediately prints the detected dominant emotion (e.g., 'happy', 'sad', 'neutral', 'angry').

How It Works

The notebook consists of a single code cell that performs the following steps:

1.  **Install Libraries:** It first installs `opencv-python-headless` (for image processing) and `deepface` (for the emotion analysis).
2.  **Define `capture_image()`:** This Python function injects JavaScript into the Colab output.
      * The JavaScript requests access to your webcam (`navigator.mediaDevices.getUserMedia`).
      * It displays a live video feed and a "Capture" button.
      * When you click **"Capture"**, it draws the current video frame onto an HTML canvas, converts it to a base64-encoded JPEG, and sends this data back to Python.
      * The Python function then decodes this data into a standard OpenCV image (NumPy array).
3.  **Define `analyze_emotion()`:** This function takes the captured image and passes it to the `DeepFace.analyze()` function, specifically asking it to perform the `emotion` action.
4.  **Execute:**
      * The script calls `capture_image()` to get a photo from the user.
      * It passes the resulting image to `analyze_emotion()`.
      * Finally, it displays the captured photo using `cv2_imshow` and prints the `dominant_emotion` from the DeepFace analysis results.

How to Use

1.  **Open the Notebook:** Ensure this notebook is open in Google Colab.
2.  **Run the Cell:** Run the single code cell.
3.  **Install Dependencies:** The cell will first take a moment to install the `deepface` and `opencv` libraries.
4.  **Grant Permission:** Your browser will pop up a request asking for **permission to use your camera**. You **must click "Allow"** for the script to work.
5.  **Capture Your Photo:** A live video feed and a "Capture" button will appear in the output. Position your face in the frame and click the **"Capture"** button.
6.  **View Results:** The video feed will disappear. Your captured photo will be displayed, followed by a line of text printing your dominant emotion, for example:
    ```
    Dominant Emotion: happy
    ```

 Dependencies

  * `opencv-python-headless`
  * `deepface`
