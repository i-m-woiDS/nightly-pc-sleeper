import os

print(" Bedtime check initiated...")

# Tell Python explicitly to send this pop-up to your main desktop screen (:0)
os.environ["DISPLAY"] = ":0"
os.environ["XAUTHORITY"] = "/home/user/.Xauthority"

popup_command = (
    'zenity --question '
    '--text="It is 11:00 PM. Your laptop will shut down in 60 seconds to help you sleep.\n\nDo you want to stay up?" '
    '--ok-label="Keep Laptop Awake" '
    '--cancel-label="Shut Down Now" '
    '--timeout=60'
)

# Launch the window and catch your choice (0 = Keep Awake, 1/Timeout = Shutdown)
response = os.system(popup_command)

if response == 0:
    print(" Shutdown cancelled. Enjoy your late night session!")
else:
    print(" No response or clicked 'Shut Down'. Powering off safely...")
    os.system("sudo /usr/sbin/poweroff")
