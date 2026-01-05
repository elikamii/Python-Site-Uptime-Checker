# Python-Site-Uptime-Checker
import requests

def check_site(url):
    try:
        response = requests.get(url)
        if response.status_code == 200:
            return "Online ✅"
        else:
            return f"Problematic (Status: {response.status_code}) ⚠️"
    except requests.ConnectionError:
        return "Offline ❌"

# Testing the function
target_site = "https://www.google.com"
print(f"Checking {target_site}...")
print(f"Status: {check_site(target_site)}")
