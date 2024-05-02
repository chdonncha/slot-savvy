SAIL=./vendor/bin/sail
ARTISAN=$(SAIL) artisan

.PHONY: install up down app test ssh log publish seed fresh migrate

build:
	$(SAIL) build
build-fresh:
	$(SAIL) build --no-cache
init:
	@make build
	@make clear-cache
	@make install
install:
	$(SAIL) up -d
	composer install
	make fresh
up:
	$(SAIL) up -d
down:
	$(SAIL) down
app:
	docker exec -ti back-end_app_1 bash
mysql:
	docker exec -ti back-end_mysql_1 bash
test:
	$(SAIL) test
ssh:
	$(SAIL) shell
log:
	$(SAIL) logs -f
seed:
	$(ARTISAN) db:seed
fresh:
	$(ARTISAN) migrate:fresh --seed
migrate:
	$(ARTISAN) migrate
clear-cache:
	$(ARTISAN) view:clear
	$(ARTISAN) config:clear
	$(ARTISAN) cache:clear
	$(ARTISAN) route:clear
