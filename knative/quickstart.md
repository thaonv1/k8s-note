# Cài đặt simple knative bằng quickstart plugin trên ubuntu 22

## Yêu cầu

- Minikube hoặc kind, bài này sẽ dùng minikube
- kubectl
- kn cli
- Sử dụng user sudo (non-root)

## Cài đặt

### kn cli

Download tại https://github.com/knative/client/releases

`wget https://github.com/knative/client/releases/download/knative-v1.11.2/kn-linux-amd64`

```
mv kn-linux-amd64 kn
chmod +x kn
mv kn /usr/local/bin
kn version
```

### Cài đặt quickstart plugin

Download tại https://github.com/knative-extensions/kn-plugin-quickstart/releases

`wget https://github.com/knative-extensions/kn-plugin-quickstart/releases/download/knative-v1.11.2/kn-quickstart-linux-amd64`

```
mv kn-quickstart-linux-amd64 kn-quickstart
chmod +x kn-quickstart
mv kn-quickstart /usr/local/bin
kn quickstart --help
```

### Cài đặt minikube

```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
sudo dpkg -i minikube_latest_amd64.deb
```

### Cài đặt kubectl

```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

### Cài đặt knative quickstart

```
kn quickstart minikube
```

Output của command trên sẽ yêu cầu bạn run minikube tunnel. Mở 1 session ssh nữa và chạy command sau

`minikube tunnel --profile knative`

Sau đó quay lại terminal chính và nhấn `Enter` để tiếp tục.

Tunnel này cần được dùng bất cứ khi nào sử dụng môi trường quickstart vì nó cho phép cluster access tới knative ingress service.