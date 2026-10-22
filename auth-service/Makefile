.PHONY: proto migrate run build tidy

proto:
	protoc --go_out=. --go_opt=paths=source_relative \
	       --go-grpc_out=. --go-grpc_opt=paths=source_relative \
	       api/proto/auth/v1/auth.proto

migrate:
	psql "$(DB_DSN)" -f migrations/001_users.sql

run:
	go run ./cmd/api

build:
	go build -o bin/auth-service ./cmd/api

tidy:
	go mod tidy