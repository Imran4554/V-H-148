# V-H-148
Visualizing Health: Advancements in Medical Image Recognition for Accurate Diagnoses.
<h1 align="center" style="border-bottom: none">
    <b>
        <a href="https://www.google.com">       Visualizing Health: Advancements in Medical Image Recognition for Accurate Diagnoses.
 </a><br>
</h1>

# [`Demo video link `](https://drive.google.com/file/d/18OMWsIhvO7ilEjD06knJlVDaesU08PHe/view?usp=sharing) 

In this insightful exploration, we uncover the transformative potential of AI-driven medical image recognition.
Delving into MRI, CT scans, X-rays, and ultrasound,we reveal how these advancements are reshaping diagnostics. 
Join us as we navigate the intersection of technology and healthcare for a glimpse into tomorrow's medical landscape.

## Team Details
`Team number` : VH148

| Name                     | Email                |
|--------------------------|----------------------|
| Shaik Imran              | 9921009016@klu.ac.in |
| Chintalapudi Sravan kumar| 9921009007@klu.ac.in |
| Md Abubakar Siddiq       | 99210041314@klu.ac.in|
| Shaik Fardeen Hussain    | 99210041314@klu.ac.in|

<div style="display: flex; flex-wrap: wrap;">

</div>

## Problem statement 
The problem is that sometimes doctors might miss things or make mistakes when looking at medical images like X-rays or scans. This can lead to people not getting the right treatment or getting it too late, which can be really bad for their health.

It's a big problem because when diseases or conditions aren't spotted early or accurately, they can get worse over time, making them harder to treat. This can cause a lot of pain and suffering for patients and can even be life-threatening in some cases.

This problem affects everyone who needs medical care, but it's especially tough for people who live far away from specialized doctors or who don't have a lot of money for healthcare. They might not have access to the best care or might struggle to afford multiple scans to get a proper diagnosis.

That's why we need a solution to improve how we look at these medical images. By using smart computer programs that can quickly and accurately analyze images, we can make sure that everyone gets the right diagnosis and treatment on time. This will help people stay healthier and save lives.
## About the project
Our project uses super-smart computer programs to help doctors see inside your body better. Here's how it works:
1. Fancy Computer Brains: We have really clever computer programs that can look at pictures of your insides, like X-rays or scans, and figure out what's going on.
2. Works with Different Pictures: It can understand lots of different kinds of pictures, like ones from MRI machines, CT scans, X-rays, and ultrasound machines. This means doctors can use it for all sorts of health problems.
3. Fast Answers: Instead of waiting a long time for a doctor to study the pictures and make a guess, our program can give answers quickly. That means you can get the help you need sooner.
4. Better Guesses: Because our program is super smart, it can make better guesses about what's wrong. This helps doctors make sure they're giving you the right treatment.
5. Helps Everyone: We want our program to be used everywhere, even in places where it's hard to get to a doctor. That way, everyone can get better healthcare, no matter where they live.
6. Always Learning: Our program is always getting smarter. It learns from looking at lots of pictures and gets better at figuring out what they mean. So, it's always improving.
7. Keeps Your Secrets Safe: We make sure that your private information stays safe. We use special rules to keep your pictures and health details private and secure.
With our project, we're making it easier for doctors to see what's wrong with you and get you the help you need faster. That's good news for everyone's health!

## Technical implemntaion 
Approach:
- Utilize advanced computer vision algorithms to analyze medical images.
- Apply machine learning techniques to train algorithms to recognize patterns indicative of different diseases.
- Develop a systematic process for accurate disease detection and diagnosis.

Solution with Technology:
1. Preprocessing of Medical Images:
   - Enhance image quality.
   - Remove noise and artifacts.
   - Normalize image size and orientation.

2. Feature Extraction:
   - Identify relevant features within the medical images.
   - Extract features using convolutional neural networks (CNNs) or other feature extraction methods.

3. Training of Machine Learning Models:
   - Use labeled medical image datasets for training.
   - Employ supervised learning algorithms such as CNNs.
   - Train the models to recognize patterns associated with various disease.

4. Disease Detection and Diagnosis:
   - Input preprocessed medical images into the trained machine learning models.
   - Allow the models to analyze the images and detect disease-related patterns.
   - Output the diagnosis based on the identified patterns.

5. Validation and Improvement:
   - Validate the accuracy and reliability of the diagnostic results.
   - Gather feedback from medical professionals.
   - Continuously improve the algorithms based on feedback and new data.

By following this approach and utilizing advanced computer vision and machine learning techniques, we have developed a robust solution for improving the accuracy, efficiency, and reliability of disease detection and diagnosis in medical imaging. Through systematic preprocessing, feature extraction, training of machine learning models, and validation processes, our technology enables accurate and timely diagnoses, ultimately enhancing patient care and outcomes.


![Screenshot 2024-03-16 234549](https://github.com/Imran4554/V-H-148/assets/163668185/3270358e-8fcf-4833-a8bc-68c3ed1582f5)




## Techstacks used 
python language ,TensorFlow, PyTorch, and  Streamlit 



## How to run locally 
explain detailed steps to run your project locally , example to run a react application 
- step 1 : run thecode in python compliler
- step 2 : upload the files in the output interface
- step 3 : based on th files uploded the possible disease will be pridicted
```

import tensorflow as tf
import cv2
import numpy as np
import streamlit as st

def classify(img):
    im = img
    lt = ["other","Bone","Brain","eye","kidney","chest","skin"] 
    im = cv2.resize(im,(52,52))
    model = tf.keras.models.load_model("all-in-one.h5",compile=False)
    result = model.predict(np.array([im]))
    a = np.argmax(result)
    c=""
    
    if a==0:
        st.write('')
        return "Provide the medical Imaging of the mentioned categories",""
        # st.write('')
    if a==1:
        st.write('')
        c= bone_net(im)
        # st.write('')
    if a==2:
        st.write('')
        c= brain_net(im)
        # st.write('')
    if a==3:
        st.write('')
        c= Eye_net(im)
        # st.write('')
    if a==4:
        st.write('')
        c= kidney_net(im)
        # st.write('')
    if a==5:
        st.write('')
        c= chest_net(im)
        # st.write('')
    if a==6:
        st.write('')
        c= skin_net(im)
    return c



def bone_net(img):
    # img = cv2.resize(img,(224,224))
    lt = ["Normal",'Fractured']
    model = tf.keras.models.load_model("fracture.h5",compile=False)
    result = model.predict(np.array([img]))
    ans = np.argmax(result)
    a=""
    b=""
    if ans==0:
        a="Normal "
        b="There is no bone facture detected"
    if ans==1:
         a="Fractured"
         b="There is  bone facture.\nconsult doctor Immediately\nApply ice: Apply ice to the affected area to reduce swelling and pain. Wrap the ice in a cloth or towel and apply it to the area for 15-20 minutes at a time, several times a day."
    return a,b

def brain_net(img):
    lt = ['pituitary', 'notumor', 'meningioma', 'glioma']
    # img = cv2.resize(img,(52,52))
    model = tf.keras.models.load_model("brain.h5",compile=False)
    result = model.predict(np.array([img]))
    ans = np.argmax(result)
    b = ""
    c = ""
    if ans==3:
        b = f"Glioma: Can range from low-grade (mild) to high-grade (severe)."
        c = "\n\nAvoid activities that could cause head injury, such as contact sports.\nTake steps to manage seizures, which can be a common symptom of gliomas.\nAvoid exposure to radiation, as this can increase the risk of developing a glioma.\nTake steps to reduce stress, which can exacerbate symptoms and affect overall health.\nWork with a healthcare provider to manage any other underlying medical conditions that could impact treatment."
    if ans==2:
        b = f"Meningioma: Most are low-grade."
        c = "\n\nAvoid activities that could cause head injury, such as contact sports.\nWork with a healthcare provider to manage any underlying medical conditions, such as high blood pressure, that could impact treatment.\nBe aware of potential symptoms, such as headaches or changes in vision, and seek medical attention promptly if they occur.\nTake steps to reduce stress, which can exacerbate symptoms and affect overall health.\nFollow a healthy lifestyle, including a balanced diet, regular exercise, and adequate sleep."
    if ans==1:
        b = "No tumor: N/A \n\n Enjoy the Life "
        c = "No Tumor has been detected \n Follow the precautions be healthy"
    if ans==0:
        b = f"Pituitary: Can be either benign or malignant."
        c = "\n\n Work with a healthcare provider to manage any underlying medical conditions, such as diabetes, that could impact treatment.\nBe aware of potential symptoms, such as headaches or changes in vision, and seek medical attention promptly if they occur.\nFollow a healthy lifestyle, including a balanced diet, regular exercise, and adequate sleep.\nTake steps to manage any hormonal imbalances that may result from the tumor.\nAvoid exposure to radiation, as this can increase the risk of developing pituitary tumors"
    return b,c

def chest_net(img):
    lt = ['PNEUMONIA', 'NORMAL']
    # img = cv2.resize(img,(224,224))
    model = tf.keras.models.load_model("chest.h5",compile=False)
    result = model.predict(np.array([img]))
    ans = np.argmax(result)
    d=""
    e=""
    if ans==0:
        d=f" Might be you are effected by pneumonia  "
        e=f"Vaccination is the best protection against pneumonia."
    if ans==1:
        d=f"Normal"
        e=f"Practice good hygiene by washing your hands frequently and avoiding touching your face"
    return d,e

def Eye_net(img):
    lt = ['glaucoma', 'normal', 'diabetic_retinopathy', 'cataract']
    # img = cv2.resize(img,(224,224))
    model = tf.keras.models.load_model("eye.h5",compile=False)
    result = model.predict(np.array([img]))
    f=""
    g=""
    if ans==3:
        f=f"You are Effected by Cataract"
        g=f'Protect your eyes from harmful UV rays with sunglasses or a hat.'
    if ans==2:
        f=f"Diaetic Retinopathy"
        g='Control your blood sugar levels to prevent diabetic retinopathy.'
    if ans==1:
        f=f"normal CONDITION"
        g='You are in Normal condition , Maintain same '
    if ans==0:
        f=f'glaucoma detected'
        g="Follow your doctor's instructions for taking glaucoma medications."
    ans = np.argmax(result)
    return f,g

def kidney_net(img):
    lt = ['Cyst', 'Tumor', 'Stone', 'Normal']
    # img = cv2.resize(img,(224,224))
    model = tf.keras.models.load_model("kidney.h5",compile=False)
    result = model.predict(np.array([img]))
    ans = np.argmax(result)
    h=""
    i=""
    if ans==0:
        h="Cyst"
        i="Avoid drinking alcohol, as it can irritate the kidneys and cause cysts to form.\nMaintain a healthy weight to reduce the risk of developing cysts."
    if ans==1:
        h="Tumor"
        i="Quit smoking to reduce the risk of kidney tumors.\nMaintain a healthy diet, rich in fruits and vegetables, to prevent the development of tumors.\nStay physically active to reduce the risk of developing tumors."
    if ans==2:
        h="Stone"
        i="Drink plenty of water to prevent the formation of kidney stones.\nLimit your intake of salt and animal protein to reduce the risk of developing stones.\nEat a diet rich in fruits and vegetables to prevent the formation of stones."
    if ans==3:
        h="Normal"
        i="You are in Normal Condition\n Be safe"
    return h,i

def skin_net(img):
    lt = ['pigmented benign keratosis', 'melano7ma', 'vascular lesion', 'actinic keratosis', 'squamous cell carcinoma', 'basal cell carcinoma', 'seborrheic keratosis', 'dermatofibroma', 'nevus']
    # img = cv2.resize(img,(224,224))
    model = tf.keras.models.load_model("skin.h5",compile=False)
    result = model.predict(np.array([img]))
    ans = np.argmax(result)
    l=""
    m=""
    if ans==0:
        l="pigmented benign keratosis"
        m="Protect your eyes from excessive exposure to sunlight or other sources of UV radiation.\nAvoid rubbing or scratching the affected area to prevent irritation or injury."
    if ans==1:
        l="melanoma"
        m="Regular eye exams with a qualified healthcare professional can help detect early signs of melanoma in the eye.\nWearing UV-protective eyewear and avoiding prolonged exposure to sunlight can help reduce the risk of developing melanoma in the eye."
    if ans==2:
        l="vascular lesion"
        m="Vascular lesions in the eye can be fragile and prone to bleeding, so it is important to avoid any activities that can increase intraocular pressure, such as heavy lifting or straining."
    if ans==3:
        l="actinic keratosis"
        m="Protect your eyes from UV radiation by wearing UV-blocking sunglasses or a hat with a brim.\nAvoid prolonged exposure to sunlight, especially during peak hours when the sun's rays are strongest."
    if ans==4:
        l="squamous cell carcinoma"
        m="Avoid smoking and limit alcohol consumption as they increase the risk of developing squamous cell carcinoma in the eye."
    if ans==5:
        l="basal cell carcinoma"
        m="Wear protective eyewear.\nMonitor your skin for any changes or abnormalities."
    if ans==6:
        l="seborrheic keratosis"
        m="Seborrheic keratosis near the eye should be examined by a healthcare professional to rule out the possibility of malignant growth.\nAvoid rubbing or scratching the affected area around the eye to prevent irritation or injury."
    if ans==7:
        l="dermatofibroma"
        m="Avoid scratching or picking at the dermatofibroma to prevent infection and further irritation.\nProtect the dermatofibroma from direct sunlight or excessive heat exposure to prevent discoloration or changes in texture."
    if ans==8:
        l="nevus"
        m="Regularly monitor the nevus and report any changes to your healthcare provider.\nProtect your eyes from excessive sun exposure by wearing sunglasses and a hat with a brim."
    return l,m
```

# What's next ?
**Future Plan for the Project:**

Moving forward, our team envisions several key updates and advancements for the "Visualizing Health" project. Firstly, we aim to further refine and optimize our medical image recognition algorithms, leveraging the latest developments in deep learning and artificial intelligence to enhance diagnostic accuracy and speed. Additionally, we plan to expand the scope of our platform to encompass a broader range of medical imaging modalities and specialties, ensuring its applicability across diverse healthcare settings. Moreover, we intend to integrate real-time feedback mechanisms and collaborative features into the platform, enabling seamless communication and knowledge sharing among healthcare professionals. Finally, we aspire to continue fostering partnerships with leading medical institutions and industry stakeholders to accelerate the adoption and integration of our technology into routine clinical practice, ultimately empowering healthcare providers to deliver more precise and personalized care to patients worldwide.
## Declaration
We confirm that the project showcased here was either developed entirely during the hackathon or underwent significant updates within the hackathon timeframe. We understand that if any plagiarism from online sources is detected, our project will be disqualified, and our participation in the hackathon will be revoked.
