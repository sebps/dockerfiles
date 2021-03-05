# Redirect
Basic protocol redirection server aiming to implicitly redirect all the incoming connexions to its configured target. Supported protocol are tcp and http.

## Usage
- Overwrite the CMD docker param with the desired settings to customize the launch command.
- The default Dockerfile CMD value is ["--sourcePort=80", "--targetPort=5000", "--targetHost=host.docker.internal"]

## Example
```
$ docker run -p 8080:80 sebpsdev/redirect --sourcePort=80 --targetPort=3000 --targetHost=host.docker.internal
```