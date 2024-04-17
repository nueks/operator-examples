## References
- https://medium.com/trendyol-tech/getting-started-to-write-your-first-kubernetes-admission-webhook-part-1-623f40c2adda
- https://sdk.operatorframework.io/docs/building-operators/golang/tutorial/



## Install Operator-sdk
https://sdk.operatorframework.io/docs/installation/

```sh
export ARCH=$(case $(uname -m) in x86_64) echo -n amd64 ;; aarch64) echo -n arm64 ;; *) echo -n $(uname -m) ;; esac)
export OS=$(uname | awk '{print tolower($0)}')
export OPERATOR_SDK_DL_URL=https://github.com/operator-framework/operator-sdk/releases/download/v1.34.1
curl -LO ${OPERATOR_SDK_DL_URL}/operator-sdk_${OS}_${ARCH}

chmod +x operator-sdk_${OS}_${ARCH} && sudo mv operator-sdk_${OS}_${ARCH} /usr/local/bin/operator-sdk
```


## Init Project

```sh
## Init Project
$ operator-sdk init --repo=github.com/nueks/memcached-operator

## Create API
$ operator-sdk create api --group cache --version v1 --kind Memcached --resource=true --controller=true
```

