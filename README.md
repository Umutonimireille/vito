Summary and Assignment.

Files
01_create_dataset.py
02_create_clusters.py
03_remove_fake_faces.py
04_train_model.py
05_make_predictions.py

Details

01_create_dataset.py
This code captures grayscale images of a person's face using a webcam, saves them, and stores corresponding metadata (customer name, image path) in a SQLite database.

------

02_create_clusters.py
This code seems to be automating the process of organizing images into clusters based on their features extracted from a VGG16 model. It allows you to identify potentially fake faces for manual review and removal, aiding in maintaining a clean dataset.

------

03_remove_fake_faces.py
This code clears out the 'dataset' directory, then populates it with images from 'dataset-clusters'. After that, it removes 'dataset-clusters'. Finally, it checks the SQLite database for records whose associated images are not in the 'dataset' folder, deletes those records, and prints a message for each deletion. This process ensures data integrity and cleanliness in the dataset.

------

04_train_model.py
This code trains a LBPH (Local Binary Patterns Histograms) face recognizer using images from a dataset. It detects faces in images using a Haar Cascade Classifier, extracts face samples, and their corresponding labels. The LBPH recognizer is then trained with these samples. If no faces are found in the dataset, it prints a corresponding message. Finally, the trained model is saved for future use.
------

05_make_predictions.py

This code utilizes a pre-trained LBPH (Local Binary Patterns Histograms) face recognizer model along with a Haar Cascade classifier for face detection. It captures frames from a webcam feed, converts them to grayscale, and detects faces. For each detected face, it predicts its identity and confidence level using the LBPH model. If the confidence level is above a threshold, it draws a rectangle around the face and displays the predicted ID along with the confidence percentage as a name tag. The process continues until the user presses 'q' to exit the loop, releasing the camera and closing all OpenCV windows.

++++++++++++++++

Next work:
Instead of displaying the ID, fetch and display info (Full Name in this case) of the person whose face is recognized based on the predicted ID (UID) from the database.
