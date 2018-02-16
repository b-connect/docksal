# Public Access via ngrok

In certain cases you may want to share or expose you local web server on the internet.
E.g. share access with a teammate or customer to demonstrate the work or discuss the progress.
Working with external web services that expect a callback URL is also generally not possible with a local environment.

## ngrok

[ngrok](https://ngrok.com/) creates a tunnel from the public internet `http://<subdomain>.ngrok.io` to a port on your local machine.
You can share the auto-generated URL with anyone to give them access to your local development environment. 
ngrok also has a web UI with an inspector for the HTTP traffic flowing over the tunnel.

## Usage

Inside the project folder run:

```bash
fin share
```

You will see a console output from the `ngrok` container.  
Use `*.ngrok.io` web address displayed there to share you project with others:

![](../_img/ngrok.png)

Use `Ctrl+C` to stop ngrok and sharing.

To access ngrok web UI, open another console window and run

```bash
fin docker ps --format "{{.Names}} {{.Ports}}" | grep ngrok
```

In the output, look for the port number assigned to the container:

```bash
$ fin docker ps --format "{{.Names}} {{.Ports}}" | grep ngrok

project_web_1_ngrok 0.0.0.0:32769->4040/tcp
``` 

Access ngrok web UI at `http://192.168.64.100:32769`
