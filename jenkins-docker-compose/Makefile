DOCKER_GID := $(shell getent group docker | awk -F: '{printf "%d",$$3}')
SERVICE := 'jenkins'

pre-run:
	echo "jenkins docker-compose start------------------"
post-run:
	echo "jenkins docker-compose success----------------"
compose-run:
	export DOCKER_GID=$(DOCKER_GID); docker-compose up --build -d;
run: pre-run compose-run post-run

pre-destroy:
	echo "jenkins docker-compose down--------------------"
post-destroy:
	echo "jenkins docker-compose down success------------"
compose-destroy:
	docker-compose down;
destroy: pre-destroy compose-destroy post-destroy

log:
	docker logs -f $(SERVICE)

exec:
	docker exec -it $(SERVICE) sh -c "((clear && bash) || (clear && sh))"
