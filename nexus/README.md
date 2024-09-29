# Nexus Repository

# Preparation
These changes are made only once in the server.
```bash
#Disable FIPS Mode 
sudo fips-mode-setup --disable
sudo systemctl reboot -i

# Generate CA for nexus
sudo keytool -genkeypair -keystore keystore.jks -storepass <password> -keypass <password> -alias jetty -keyalg RSA -keysize 2048 -validity 5000 -dname "CN=nexus, OU=DevDiv, O=Turkey, L=Istanbul, ST=Istanbul, C=TR" -ext "SAN=DNS:nexus,IP:127.0.0.1" -ext "BC=ca:true"
```

# Installation
```bash
# Run nexus container
docker compose up -d

# Stop nexus container
docker compose down -v
```
