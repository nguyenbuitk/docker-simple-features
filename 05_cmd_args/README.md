## Default image of ubuntu
docker run ubuntu

```bash ubuntu image
Layers (6)
ARG RELEASE
ARG LAUNCHPAD_BUILD_ARCH
LABEL org.opencontainers.image.ref.name=ubuntu
LABEL org.opencontainers.image.version=22.04
ADD file:0ad2ee2cfb186802f49c9bf4148674d1c6fc201f83478ec01ffaa7086d491323 in /
CMD ["/bin/bash"]
```

CMD ["bash"]: listen input from terminal

How do specify a different command to start conatainer
-> append the command: 
```bash
docker run ubuntu [COMMAND]
docker run ubuntu sleep 5
```
-> sau khi chờ 5s sẽ exit -> vậy có cách nào để chạy lâu dài không?

## Các kiểu chỉnh sửa command trong layer của docker image 
CMD command1 param1         | CMD sleep 5

CMD ["command1", "param1"]  | CMD ["sleep", "5"]

## Các case
image ban đầu:
```bash
FROM ubuntu
CMD sleep 5
```

command build image

```bash
docker build -t sleeper-ubuntu .
```

### Case 1: Trường hợp muốn change command từ 5 thành số khác
```bash
docker run ubuntu-sleeper sleep 10
```

### Case 2: trường hợp không muốn truyền vào `sleep`, chỉ muốn truyền vào số 10
-> ENTRYPOINT sinh ra để giải quyết việc này, entrypoint không bị ghi đè, còn command thì bị ghi đè
```bash
FROM ubuntu
ENTRYPOINT ["sleep"]
```

```bash
docker run ubuntu-sleeper 10
```

### Case 3: trường hợp docker run ubuntu-sleeper mà không truyền vào args thì sao?
Lúc này nếu chạy ``docker run ubuntu-sleeper`` sẽ gặp lỗi
```bash
sleep: missing operand
Try 'sleep --help' for more information
```

-> cần khắc phục bằng cách sẽ sử dụng cả CMD và ENTRYPOINT
```bash
FROM ubuntu
ENTRYPOINT ["sleep"]
CMD ["5"]
```
Nếu run command `docker run ubuntu-sleeper 10` thì CMD trong image sẽ bị overwrite