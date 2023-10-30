# Install a trusted root CA on Linux

## Summary

To install a trusted root certificate authority (CA) on Linux, you need to copy the certificate to `ca-certificates` and apply an update.

* Copy `.crt` to `/usr/local/share/ca-certificates`
* Then run `update-ca-certificates`

For this useful for getting rid of a insecure connection warning when you are trying to access your router.

## Appendix

For ASUS router certificates, convert .pem to .crt (PER Base64 format): 

```shell
openssl x509 -outform der -in cert.pem -out cert-asus.crt
sudo update-ca-certificates
```

To reinstall default certificates on your system, reinstall ca-certificates:

```shell
sudo apt-get reinstall -y ca-certificates
```

## References

https://ubuntu.com/server/docs/security-trust-store
https://askubuntu.com/questions/1215017/install-crt-certificate-on-ubuntu-18-04 
https://blog.nuvotex.de/adding-trusted-root-ca-certificates-on-linux/
https://stackoverflow.com/questions/13732826/convert-pem-to-crt-and-key (conversion


