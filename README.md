import smtplib
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText

def send_email(subject, body, to_email):
    # Email account credentials
    from_email = 'almuslimkarpet@gmail.com '
    password = 'your_password'

    # Setting up the MIME
    msg = MIMEMultipart()
    msg['From'] = from_email
    msg['To'] = to_email
    msg['Subject'] = subject

    # Adding the body to the email
    msg.attach(MIMEText(body, 'plain'))

    try:
        # Connecting to the server
        server = smtplib.SMTP('smtp.example.com', 587)  # Replace with your SMTP server and port
        server.starttls()
        server.login(from_email, password)
        
        # Sending the email
        server.send_message(msg)
        print("Email sent successfully")
        
    except Exception as e:
        print(f"Failed to send email: {e}")
        
    finally:
        server.quit()

# Usage
send_email('Test Subject', 'This is a test email body.', 'recipient@example.com')
