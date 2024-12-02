![image](https://github.com/user-attachments/assets/bc648df3-1dc7-4f46-b4e2-1d6f9fb0d2e6)

```bash
APT_KEY_URL="https://apt.sonaric.xyz/repo-signing-key.pgp"
APT_DOWNLOAD_URL="https://apt.sonaric.xyz"

if ! grep -q $APT_DOWNLOAD_URL "/etc/apt/sources.list.d/sonaric.list"; then
    apt_repo="deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/sonaric.gpg] $APT_DOWNLOAD_URL stable main"
    curl -fsSL "$APT_KEY_URL" | gpg --dearmor --yes -o /etc/apt/keyrings/sonaric.gpg
    chmod a+r /etc/apt/keyrings/sonaric.gpg
    echo "$apt_repo" > /etc/apt/sources.list.d/sonaric.list
    apt-get clean
fi
apt-get update
apt-get install sonaricd sonaric
```

![image](https://github.com/user-attachments/assets/ac8f1304-ee76-4b4f-b506-fdc79bc35ad4)

```bash
sudo rm -f /etc/apt/sources.list.d/sonaric.list
sudo apt-get clean
```
