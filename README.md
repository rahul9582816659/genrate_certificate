# Generate a Trusted SSL Certificate

This repository contains a script that will generate a trusted ssl certificate which can be used for local software development.

```
git clone https://github.com/RubenVermeulen/generate-trusted-ssl-certificate.git
cd <PATH_TO_REPO_FOLDER>/generate-trusted-ssl-certificate
bash generate.sh
```

## Configuration

You can adjust the `[dn]` part of the `openssl-custom.cnf` file to whatever you prefer.

```
[dn]
C = <COUNTRY>
ST = <STATE>
L = <LOCALITY / CITY>
O = <ORGANIZATION>
OU = <ORGANIZATION_UNIT>
emailAddress = <EMAIL_ADDRESS>
CN = <HOSTNAME / IP_ADDRESS>
``` 


Simple fix is while running

ng s -o

Run with extra attribute

ng s -o ---ssl true //It will run on https://localhost:4200. But, if you have .crt and .key file, then add that attribute also

You will see in browser it will start with https still it says "not secure"

This is sufficient if you just wanna run on https and you don't care "not secure", else proceed >>

ng s -o ---ssl true --ssl-key <path to key file>  --ssl-cert <path to crt file> or give relative path to .key and .crt file

If you don't want to give this attribute each time or running nginx server for angular, then add these attributes in angular.json or angular-cli.json depending upon angular version

"serve": 
 {
      "builder": "@angular-devkit/build-angular:dev-server",
      "options": 
      {
        "browserTarget": "ideationapp:build",
        "ssl": true,
        "sslKey": "ssl/server.key",
        "sslCert": "ssl/server.crt",
      }
}
ssslkey and sslcert is not required if you don't have .key and .crt file

Here, I kept both file in ssl dir where src, e2e and angular.json is there

Then only ng s -o is sufficient

How to create temporary fix for localhost for only your machine or only for one user

require
Git bas (Download fom here)
Now go to Gitbash and type this command one at a time

git clone https://github.com/RubenVermeulen/generate-trusted-ssl-certificate.git(cloned to local computer)
cd generate-trusted-ssl-certificate(Going to application path)
bash generate.sh(starting shell script wher we called openssl)
The cloned application use openssl(software library for applications that secure communications over computer networks against eavesdropping or need to identify the party at the other end) to generate .crt and .key file

It will create server.key & server.crt file

Now click on server.crt

For OS X
1.Double click on the certificate (server.crt)

2.Select your desired keychain (login should suffice)

3.Add the certificate

4.Open Keychain Access if it isn’t already open

5.Select the keychain you chose earlier

6.You should see the certificate localhost

7.Double click on the certificate

8.Expand Trust

9.Select the option Always Trust in When using this certificate

10.Close the certificate window

Windows 10
1.Double click on the certificate (server.crt)

2.Click on the button “Install Certificate …”

3.Select whether you want to store it on user level or on machine level

4.Click “Next”

5.Select “Place all certificates in the following store”

6.Click “Browse”

7.Select “Trusted Root Certification Authorities”

8.Click “Ok”

9.Click “Next”

10.Click “Finish”

11.If you get a prompt, click “Yes”

create ssl dir
put cert & key
ng serve --ssl true --ssl-cert "ssl\server.crt" --ssl-key "ssl\server.key"