import pyfiglet
from colorama import init, Fore, Style
import os
import sys
import time
import smtplib
from email.message import EmailMessage

# Initialize colorama
init(autoreset=True)

# About section
about_lines = [
    "👤 Monir Hasan — Sales Manager & Affiliate Specialist at iMonetizeIt.",
    "💼 5+ years in digital marketing & CPA monetization.",
    "📍 Based in Bangladesh | 🎓 BBA in Accounting (ongoing)."
]

# Disclaimer
disclaimer = Fore.YELLOW + Style.BRIGHT + (
    "\n⚠️ Disclaimer: This is for educational/demo purposes only.\n"
    "❌ Do NOT use this to send unsolicited emails. Misuse may be illegal.\n"
)

# ASCII Banner (Your Name)
ascii_banner = pyfiglet.figlet_format("Monir Hasan")

def show_banner():
    os.system('cls' if sys.platform.startswith('win') else 'clear')
    print(Fore.MAGENTA + ascii_banner)   # Big Name Banner
    for line in about_lines:
        print(Fore.CYAN + line)          # About Info
    print(disclaimer)                    # Disclaimer in Yellow

def send_test_email():
    print(Fore.MAGENTA + "📧 Email Sending Demo\n")
    print(Fore.CYAN + "🔑 Reminder: Use your 16-character Gmail App Password (not your normal Gmail password).\n")

    email = input("Your Gmail Address: ")
    user = input("Your Name: ")
    passwd = input("Your Gmail App Password (paste here): ")
    to = input("Recipient Email: ")
    subject = input("Email Subject: ")   # ✅ Added custom subject
    body = input("Message: ")
    total = int(input("How many emails to send? "))

    try:
        with smtplib.SMTP("smtp.gmail.com", 587) as server:
            server.starttls()
            server.login(email, passwd)

            for i in range(1, total + 1):
                msg = EmailMessage()
                msg["Subject"] = f"{subject} (#{i})"
                msg["From"] = f"{user} <{email}>"
                msg["To"] = to
                msg.set_content(body)

                server.send_message(msg)
                print(Fore.GREEN + f"✅ Email {i}/{total} sent successfully!")
                time.sleep(1)  # delay so Gmail doesn’t block you

    except smtplib.SMTPAuthenticationError:
        print(Fore.RED + "\n❌ Authentication failed. Use an App Password, not your main Gmail password.")
    except KeyboardInterrupt:
        print("\n[-] Canceled by user")
        sys.exit()
    except Exception as e:
        print(Fore.RED + f"\n⚠️ Error: {e}")
        sys.exit()

if __name__ == "__main__":
    show_banner()
    send_test_email()
