# 🚀 Python (Flask) Application Deployment on AWS EC2 with Gunicorn






# 📖 Introduction







This project is a simple Python web application built with Flask and deployed on an AWS EC2 instance. The application runs on port 5000 and returns a message in the browser when the server's public IP is opened.
The code is pulled from GitHub onto the EC2 server, dependencies are installed with pip using requirements.txt, and the app is served with Gunicorn, a production-grade WSGI server, instead of Flask's built-in development server.
The goal of this project is to practice deploying a Python application on the AWS cloud, from launching the server and opening the required port to verifying the live output in the browser.





# 🛠️ Technologies Used


AWS EC2 Cloud server to host the application



Amazon Linux 2023 Operating system of the server



Python 3.9 Programming language



Flask 3.1.3 Web framework used to build the app



Gunicorn 23.0.0 Production WSGI server to run the Flask app




pip & venv Package manager and virtual environment




Git & GitHub Version control and code hosting






# 🏗️ Architecture Diagram (AWS)


<img width="1280" height="720" alt="WhatsApp Image 2026-10-12 at 21 52 49" src="https://github.com/user-attachments/assets/6857268d-4cb5-42e9-a2f4-a5fc1472688e" />

Flow: User (Browser) → Internet → Security Group (port 5000) → Gunicorn → Flask app (app.py) → Response back to the browser.




# ⚙️ Setup & Installation (on EC2 Server)


    insatll python3 and python3-pip


    clone file from github  app.py  requirements.txt


   ###  5. Create and activate a virtual environment


    python3 -m venv darshan

    sudo bash darshan/bin/activate


  ### ⚠️ Important: Confirm the actual package name and version. Do not use Flask==8.1.8 unless that is the version you really installed and it exists for your environment.

<img width="1920" height="1080" alt="Screenshot (17)" src="https://github.com/user-attachments/assets/ce4a052e-0af6-4453-91ab-bb4fedec92e8" />


   # 6. Install dependencies

  #### pip install -r requirements.txt

<img width="1920" height="1080" alt="Screenshot (22)" src="https://github.com/user-attachments/assets/758aa230-8e74-4ed4-94d6-cd02b51a03dd" />


Flask's built-in server is only for development. For deployment, Gunicorn is used (next step).

###   Run file


python3 app.py


<img width="1920" height="1080" alt="Screenshot (19)" src="https://github.com/user-attachments/assets/b39cbf4c-bce9-47b0-a0b0-a3f81ce7f67f" />










## 8. Run the app with Gunicorn in the background
 

   gunicorn --bind 0.0.0.0:5000 app:app --daemon


   <img width="1920" height="1080" alt="Screenshot (20)" src="https://github.com/user-attachments/assets/72e76126-8d69-4390-89ac-1f9e63537a72" />



   


     --daemon keeps the server running in the background after the terminal is closed


  ### Open in the browser
  
  
  http://<EC2-PUBLIC-IP>:5000



# 📤 Output




The Flask app responds with a text message, which is displayed in the browser:



<img width="1920" height="1080" alt="Screenshot (21)" src="https://github.com/user-attachments/assets/b29fb32e-7103-49b5-bd2a-104982e0e5fb" />







# 🧩 Challenges Faced



Amazon Linux uses python3, so used python3 instead of python



ModuleNotFoundError: No module named 'flask'



Installed the dependencies using pip install -r requirements.txt



No matching distribution found for click==8.4.1




That version does not exist, so changed it to click==8.1.8 in requirements.txt



gunicorn: command not found



Gunicorn was not installed yet, so installed it through requirements.txt first




# ✅ Conclusion




In this project, a Python Flask application was successfully deployed on an AWS EC2 server. The code was cloned from GitHub, dependencies were installed with pip, and the application was served in the background using Gunicorn. The output in the browser confirms that the server, the Security Group rules and the application all work correctly.
Through this project I learned:
Launching an EC2 instance and opening a custom port in the Security Group
Setting up Python, pip and virtual environments on a Linux server
Fixing real errors such as missing modules and wrong package versions
Why a production WSGI server (Gunicorn) is used instead of Flask's development server



## Future improvements: 

add Nginx as a reverse proxy on port 80, enable HTTPS with SSL, run Gunicorn as a systemd service so it restarts after a reboot, and automate deployment with a CI/CD pipeline (Jenkins / GitHub Actions).



## 👤 Author



### Darshan Patil
