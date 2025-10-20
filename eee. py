import socket
import requests
import subprocess
import re
class SystemInfo:
    def get_local_ip(self):
            s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
            s.connect(("8.8.8.8", 80))
            local_ip = s.getsockname()[0]
            s.close()
            return local_ip
            
    def get_public_ip(self):
            response = requests.get('https://api.ipify.org')
            return response.text
            
    def get_mac_address(self):
                command = "getmac"
                result = subprocess.check_output(command, shell=True, encoding='utf-8')
                return result
                
    def get_wifi_password(self, wifi_name):
        command = f'netsh wlan show profile name="{wifi_name}" key=clear' 
        result = subprocess.check_output(command, shell=True, encoding='utf-8')
        key_content_match = re.search(r"Key Content\s+:\s+(.*)", result)
        if key_content_match:
            password = key_content_match.group(1).strip()
            return password
wifi_name_input = input("Enter Name Of Wifi : ") 
collector = SystemInfo()
print(f"Local IP : {collector.get_local_ip()}\nPublic IP : {collector.get_public_ip()}\n{collector.get_mac_address()}\nWifi Pass: {collector.get_wifi_password(wifi_name_input)}")
