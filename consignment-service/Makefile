build:
	protoc -I. \
		--go_out=plugins=micro:$(GOPATH)/src/github.com/mramsden/shipping/consignment-service \
		proto/consignment/consignment.proto
	GOOS=linux GOARCH=amd64 go build
	docker build -t shipping/consignment-service .

run:
	docker run -p 50051:50051 \
		-e MICRO_SERVER_ADDRESS=:50051 \
		-e MICRO_REGISTRY=mdns shipping/consignment-service
