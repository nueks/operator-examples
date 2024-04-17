## References
- https://book.kubebuilder.io/quick-start.html

## Env

Install Kubebuider

```sh
# download kubebuilder and install locally.
$ curl -L -o kubebuilder "https://go.kubebuilder.io/dl/latest/$(go env GOOS)/$(go env GOARCH)"
# chmod +x kubebuilder && mv kubebuilder /usr/local/bin/
$ sudo install -m +x kubebuilder /usr/local/bin
```

## Init

프로젝트 생성

```sh
mkdir memcached
cd memcached
go mod init example.com/memcached-operator
kubebuilder init --domain example.com
```

crd와 custom controller 생성
```sh
kubebuilder create api --group cache --version v1alpha1 --kind Memcached
```

## Develop

- api/v1alpha1/memcached_types.go 파일 편집. CRD 에 사용될구조체
- `make generate` -> zz_generated.deepcopy.go 파일 생성
- `make manifests` -> config/crd/bases/cache.example.com_memcacheds.yaml 생성
- internal/controller/memcached_controller.go 에 reconciler 코드.
  특히 SetupWithManager 코드는 다름 링크의 내용 참고
  https://pages.oss.navercorp.com/AiSuite/study/#/kubernetes_operator_practice?id=triggering-reconciliation