BUILDX=docker buildx build --platform linux/amd64,linux/arm64

.PHONY: base bird quagga frr sdn p4 all pushall all-multi create-builder base-multi bird-multi quagga-multi frr-multi sdn-multi p4-multi delete-builder

all: base bird quagga frr sdn p4
all-multi: create-builder base-multi bird-multi quagga-multi frr-multi sdn-multi p4-multi delete-builder

pushall:
	docker push kathara/base:debian10
	docker push kathara/bird:debian10
	docker push kathara/quagga:debian10
	docker push kathara/frr:debian10
	docker push kathara/sdn:debian10
	docker push kathara/p4:debian10
	docker image tag kathara/base:debian10 kathara/base:latest
	docker push kathara/base:latest
	docker image tag kathara/bird:debian10 kathara/bird:latest
	docker push kathara/bird:latest
	docker image tag kathara/quagga:debian10 kathara/quagga:latest
	docker push kathara/quagga:latest
	docker image tag kathara/frr:debian10 kathara/frr:latest
	docker push kathara/frr:latest
	docker image tag kathara/sdn:debian10 kathara/sdn:latest
	docker push kathara/sdn:latest
	docker image tag kathara/p4:debian10 kathara/p4:latest
	docker push kathara/p4:latest

base:
	docker build -t kathara/base:debian10 base

bird: base
	docker build -t kathara/bird:debian10 bird

quagga: base
	docker build -t kathara/quagga:debian10 quagga

frr: base
	docker build -t kathara/frr:debian10 frr

sdn: base
	docker build -t kathara/sdn:debian10 sdn

p4: base
	docker build -t kathara/p4:debian10 p4

base-multi: create-builder
	$(BUILDX) -t kathara/base:debian10 -t kathara/base:latest --push base

bird-multi: create-builder base-multi
	$(BUILDX) -t kathara/bird:debian10 -t kathara/bird:latest --push bird

quagga-multi: create-builder base-multi
	$(BUILDX) -t kathara/quagga:debian10 -t kathara/quagga:latest --push quagga

frr-multi: create-builder base-multi
	$(BUILDX) -t kathara/frr:debian10 -t kathara/frr:latest --push frr

sdn-multi: create-builder base-multi
	$(BUILDX) -t kathara/sdn:debian10 -t kathara/sdn:latest --push sdn

p4-multi: create-builder base-multi
	$(BUILDX) -t kathara/p4:debian10 -t kathara/p4:latest --push p4

create-builder:
	docker buildx create --name kat-builder --use
	docker buildx inspect --bootstrap

delete-builder:
	docker buildx rm kat-builder
