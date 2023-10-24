# **`Auto-Run Python Script on Jetson Nano Startup`**

Automate the execution of your Python script on Jetson Nano startup with this simple guide. By configuring a systemd service, you can ensure that your script runs seamlessly every time the system boots up, eliminating the need for manual intervention.


### Getting Started

### Open a terminal on your Jetson Nano


```python
Ctrl + Alt + T
```

### Navigate to the systemd service directory


```python
cd /etc/systemd/system/
```

### Create a new service file


```python
sudo nano myscript.service
```

### Add the following content to the service file


```python
[Unit]
Description=My Script Service
After=network.target

[Service]
ExecStart=/usr/bin/python3 /path/to/your/script.py
WorkingDirectory=/path/to/your/script/directory
Restart=always
User=yourusername
Group=yourusername

[Install]
WantedBy=multi-user.target
```

Save the file and exit the text editor:
*   Ctrl + S -> to save the file
*   Ctrl + X -> to exit

Note: Replace **"myscript.service"** with the desired service name, **"script.py"** with the name of your program, and **"/path/to/your/script"** with the actual path where your program is located.

### Reload systemd to make it aware of the new service


```python
sudo systemctl daemon-reload
```

### Enable and start the service


```python
sudo systemctl enable myscript.service
sudo systemctl start myscript.service
```

### Disable and stop the service


```python
sudo systemctl disable myscript.service
sudo systemctl stop myscript.service
```

### Check the status and if the service is enable


```python
sudo systemctl is-enabled startButton.service
sudo systemctl status startButton.service
```

### Example

As an example, let's say you have a script named button.py located in the directory /home/username/my-detection. Here's how you would configure the service:


```python
cd /etc/systemd/system/

sudo nano startButton.service

[Unit]
Description=My Script Service
After=network.target

[Service]
ExecStart=/usr/bin/python3 /home/username/my-detection/button.py
WorkingDirectory=/home/username/my-detection
Restart=always
User=username

[Install]
WantedBy=multi-user.target
```

### Clean Up

If you want to remove the service, use the following command:


```python
sudo rm /etc/systemd/system/myscript.service
```
