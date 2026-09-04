Dockerfile is recipe from which we build the docker image.
Simple example:
1) create simple bash script for greeting and make it executable:
	- `mkdir myapp && cd myapp && vim hello`
	- put inside `shebang` and  `echo 'Hello`
	- `chmod +x hello`
2) create Dockerfile:
```
FROM ubuntu:24.04

WORKDIR /app

COPY hello .

CMD ["./hello"]
```
3) `docker build -t myapp:1.0.0 .`
	- `-t` add tag
	- `.` use current directory as build context

Links:

202609021234

