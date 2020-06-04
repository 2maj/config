#Configuration of Ngrok

##Require
- Create account (email, password) : optional
- Download ngrok
    - https://ngrok.com/download
    
## Start
- Unzip ngrok : unzip /path/to/ngrok.zip
- put it in you */usr/local/bin/* to allow to you run easily from you Terminal/console
- run your local server app keep safe your server port
- run the cmd :
    > ngrok http [your_server_port]

##Optional
- **If you need to customized your the link provided by ngrok**
    - get your token from ngrok account
    - run :
    > ngrok authtoken <YOUR_AUTH_TOKEN>
