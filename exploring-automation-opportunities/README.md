<h1>
  <span class="headline">Automating Tasks with Python</span>
  <span class="subhead">Exploring Automation Opportunities</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to apply python automation concepts to different problems.

You've already seen how Python can be a helpful tool for automating tasks related to APIs, web scraping, and data analysis. But the possibilities don't stop there! Python's versatility makes it an ideal language for automating a wide range of tasks across various domains.

Let's explore a few more exciting areas where Python can be leveraged for automation. These examples will help spark your creativity and get you thinking about how you can apply Python to streamline your own workflows and projects.

# Automating Image Manipulation

Picture this: you have a collection of images that need to be resized, converted to a different format, or have a watermark applied. Doing this manually for each image would be a tedious and time-consuming task. But fear not! Python comes to the rescue with the powerful Pillow library, making image manipulation a breeze.

Let's say you need to create thumbnails for a large set of images. Here's how Python can automate the process:

``` python
from PIL import Image
import os

def create_thumbnails(source_dir, output_dir, size=(128, 128)):
    if not os.path.exists(output_dir):
        os.makedirs(output_dir)
    
    for filename in os.listdir(source_dir):
        if filename.endswith(".jpg") or filename.endswith(".png"):
            image_path = os.path.join(source_dir, filename)
            thumbnail_path = os.path.join(output_dir, f"thumb_{filename}")
            
            with Image.open(image_path) as image:
                image.thumbnail(size)
                image.save(thumbnail_path)

# Usage
source_directory = "path/to/your/images"
output_directory = "path/to/your/thumbnails"
thumbnail_size = (128, 128)

create_thumbnails(source_directory, output_directory, thumbnail_size)
```

In this code, we use the Pillow library (imported as `PIL`) to handle image operations. The `create_thumbnails` function takes the source directory, output directory, and desired thumbnail size as parameters. It iterates over the image files in the source directory, opens each image using `Image.open()`, resizes it using the `thumbnail()` method, and saves the resized image to the output directory with a "thumb_" prefix.

Imagine the time saved by automating this process, especially when dealing with hundreds or thousands of images! Python's Pillow library provides a wide range of image manipulation capabilities, such as cropping, rotating, applying filters, and more. By harnessing these functionalities, you can automate complex image workflows efficiently.

# Automating Email Notifications

Sending automated email notifications is another useful application of Python. Whether you want to send alerts, reports, or updates, Python's `smtplib` library makes it easy to automate email communication.

Here's a simple example of how you can send an email notification using Python:

``` python
import smtplib
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart

def send_email(subject, body, sender, recipients):
    msg = MIMEMultipart()
    msg['Subject'] = subject
    msg['From'] = sender
    msg['To'] = ', '.join(recipients)
    
    msg.attach(MIMEText(body, 'plain'))
    
    smtp_server = 'smtp.example.com'
    smtp_port = 587
    smtp_username = 'your_username'
    smtp_password = 'your_password'
    
    with smtplib.SMTP(smtp_server, smtp_port) as server:
        server.starttls()
        server.login(smtp_username, smtp_password)
        server.send_message(msg)

# Usage
subject = "Automated Email Notification"
body = "This is an automated email sent using Python!"
sender = "sender@example.com"
recipients = ["recipient1@example.com", "recipient2@example.com"]

send_email(subject, body, sender, recipients)
```

In this example, we define a function called `send_email` that takes the email subject, body, sender, and recipients as parameters. It uses the `MIMEMultipart` and `MIMEText` classes from the email module to construct the email message. The `smtplib` library is then used to establish a connection with an SMTP server, authenticate with the provided credentials, and send the email.

By automating email notifications, you can keep yourself or others informed about important events, send scheduled updates, or trigger alerts based on specific conditions.

# Future Automation Opportunities

These are just a few examples of the many tasks you can automate using Python. The possibilities are endless, and Python's library ecosystem provides tools for automating tasks in various domains, such as system administration, network management, GUI automation, and more.

As you continue your Python automation journey, keep an eye out for repetitive tasks in your daily workflow or projects. Chances are, there's a way to automate them using Python! Don't be afraid to explore new libraries, experiment with different approaches, and leverage the power of automation to save time and effort.
