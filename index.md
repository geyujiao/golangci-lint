
### 1. 安装
本地安装
```
go get -u github.com/golangci/golangci-lint/cmd/golangci-lint
```
本地安装完成后，你使用golangci-lint --version是看不到它的版本信息的。命令行会提示错误：Error：unknown flag： --version。要想看到可以执行下面的命令。
```
cd $(go env GOPATH)/src/github.com/golangci/golangci-lint/cmd/golangci-lint
go install -ldflags "-X 'main.version=$(git describe --tags)' -X 'main.commit=$(git rev-parse --short HEAD)' -X 'main.date=$(date)'"
```
### 2. 检测代码
```
golangci-lint run
```
支持的linter
可以通过命令golangci-lint help linters查看它支持的linters。你可以传入参数-E/--enable来使某个linter可用，也可以使用-D/--disable参数来使某个linter不可用。例如：
```
golangci-lint run --disable-all -E errcheck
```
