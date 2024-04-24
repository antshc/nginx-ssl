## Resources
* https://gist.github.com/dahlsailrunner/679e6dec5fd769f30bce90447ae80081
* https://support.kerioconnect.gfi.com/hc/en-us/articles/360015200119-Adding-Trusted-Root-Certificates-to-the-Server

### Install packages
```
sudo apt update && sudo apt update && sudo apt install openssl -y && apt install ca-certificates
```
### Generate SSL certificates 
```
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout private.key -out localhost.crt -config localhost.conf -passin pass:dev
```

## Import SSL certificates to Debian
### Create ssl directory
```
 sudo mkdir -p /usr/local/share/ca-certificates/
```
### Copy certificates
```
sudo cp /mnt/c/projects/ngingxssl/localhost.pfx /usr/local/share/ca-certificates/localhost.pfx
sudo cp /mnt/c/projects/ngingxssl/localhost.key /usr/local/share/ca-certificates/localhost.key

sudo cp localhost.crt /usr/local/share/ca-certificates/localhost.crt
sudo cp localhost.pem /usr/local/share/ca-certificates/localhost.pem
sudo cp localhost.crt /etc/ssl/certs/localhost.crt
sudo cp localhost.pem /etc/ssl/certs/localhost.pem
```

### Update certificates
```
sudo update-ca-certificates
```