# Config database

```
sudo apt-get install sqlite3 db.sqlite
sqlite3 db.sqlite
> create table categories (id string, name string, description string);
```

# Generating proto

```
go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.28
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.2

export PATH="$PATH:$(go env GOPATH)/bin"

protoc --go_out=. --go-grpc_out=. proto/course_category.proto
```

# Installing evans

ref: https://github.com/ktr0731/evans/issues/150#issuecomment-465394581

```
$ curl -L 'https://github.com/ktr0731/evans/releases/download/0.6.11/evans_linux_amd64.tar.gz' | tar xvzf -
$ sudo mv evans /usr/local/bin/evans
$ evans
```

# Using evans

```
go run cmd/grpcServer/main.go

evans --reflection

> service CategoryService
> call CreateCategory
    > name (TYPE_STRING) => xx
    > description (TYPE_STRING) => xx
```

output 👇

```
{
  "category": {
    "id": "c571a21e-f03e-453a-ac75-d8add4821f07",
    "name": "xx",
    "description": "xx"
  }
}
```