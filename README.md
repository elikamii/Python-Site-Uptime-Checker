import requests
import time

def monitor_sites(urls):
    print(f"{'URL':<30} | {'Status':<10} | {'Response Time':<15}")
    print("-" * 60)
    
    for url in urls:
        try:
            start_time = time.time()
            response = requests.get(url, timeout=5)
            end_time = time.time()
            
            # Calculate duration in seconds
            duration = round(end_time - start_time, 3)
            status = "ONLINE" if response.status_code == 200 else f"HTTP {response.status_code}"
            
            print(f"{url:<30} | {status:<10} | {duration}s")
            
        except requests.RequestException:
            print(f"{url:<30} | {'OFFLINE':<10} | {'N/A':<15}")

# List of websites to monitor
sites_to_check = [
    "https://www.google.com",
    "https://www.github.com",
    "https://www.python.org",
    "https://this-site-does-not-exist.com"
]

monitor_sites(sites_to_check)
