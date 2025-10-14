import hashlib
import requests
pwd = input("Enter Pass To Cheack :")
def check_password(password):
    sha = hashlib.sha1(password.encode('utf-8')).hexdigest().upper()
    passchr5 = sha[:5] 
    bakpass = sha[5:]
    resp = requests.get(f"https://api.pwnedpasswords.com/range/{passchr5}")
    resp.raise_for_status()
    for line in resp.text.splitlines():
        offcpass, count = line.split(':')
        if offcpass == bakpass:
            return int(count)
    return 0
times = check_password(pwd)
if times:
    print(f"Dont Use it Leaked {times} times")
else:
    print("Not Leaked Coool:)")
