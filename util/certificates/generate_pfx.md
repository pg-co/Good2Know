# Generate a PFX (PKCS#12)

### Generating a Private-Key

```bash
sudo openssl genrsa 2048 > private.pem
```

### Generate X509 Certificate

```bash
sudo openssl req -new -x509 -nodes -days <NUMBER_OF_DAYS> -key private.pem -out cert.pem 
```

### Generate PFX (PKCS#12)

```bash
sudo openssl -export -in cert.pem -inkey private.pem -out cert.pfx
```