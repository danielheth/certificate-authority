# Certificate Authority
This is a Drupal module with the simple purpose of creating a front end UI for me to use when creating Website SSL Certificates for my Lab environment.

I've pushed all commands to generate a certificate and key within a single, very simple, shell script.  This shell script is kept in the file system and this Drupal module simply calls that script passing the hostname I entered into the form.  

The certificate and key are provided to me as a link for me to immediately download.




## Create your own CA
I used the following openssl commands to create my own certificate authority:

### Create Private CA Key:
openssl genrsa -des3 -out ca.key 4096

### Create new Certificate valid for 10 years
openssl req -new -x509 -extensions v3_ca -key ca.key -out ca.crt -days 3650


## Installation
Place both the ca.key and ca.crt file within the c:\CA directory on your Drupal server.  Then copy the certauth.info and certauth.module files into your htdocs\modules\certauth\   directory.  Log into Drupal and enable this module.

## Testing
Browse to http(s)://[your drupal server]/certauth/form and fill out the form and hit submit.  You'll receive a link to the completed zip bundle which contains your new certificate, the related key and the CA public certificate.
