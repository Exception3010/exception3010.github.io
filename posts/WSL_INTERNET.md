# Fixing WSL Internet Connectivity Issues

Sometimes WSL works fine on Windows, but inside your Linux environment you have no internet access.  
Commands like `apt update`, `curl`, or `git clone` fail even though Windows itself is online.

---

## 🔍 Symptoms
- Package managers (`apt`, `dnf`, etc.) cannot connect.  
- `ping 8.8.8.8` fails.  
- Git or other network tools show connection errors.  

---

## 🛠 Solution
The fix is to configure WSL’s networking and DNS tunneling.  
Create or edit this file:

```

C:\Users<YourUser>.wslconfig

````

Set the content to:

```ini
[experimental]
dnsTunneling=true
autoProxy=true

[wsl2]
networkingMode=mirrored
````

Restart WSL:

```powershell
wsl --shutdown
```

Reopen your Linux distribution and test connectivity again.

---

## ✅ Result

* Internet access is restored for commands like `apt`, `curl`, `git`, etc.
* No need to manually adjust DNS or proxy settings every session.

---

## 📌 Takeaway

If your WSL environment suddenly loses internet access,
resetting `.wslconfig` with **DNS tunneling** and **mirrored networking** is a reliable fix.
