.DEFAULT_GOAL := list
list:
	@printf "%-20s %s\n" "Target" "Description"
	@printf "%-20s %s\n" "------" "-----------"
	@make -pqR : 2>/dev/null \
			| awk -v RS= -F: '/^# File/,/^# Finished Make data base/ {if ($$1 !~ "^[#.]") {print $$1}}' \
			| sort \
			| egrep -v -e '^[^[:alnum:]]' -e '^$@$$' \
			| xargs -I _ sh -c 'printf "%-20s " _; make _ -nB | (grep -i "^# Help:" || echo "") | tail -1 | sed "s/^# Help: //g"'
test:
	@# Help: Run tests
	@pnpm test
test/e2e:
	@# Help: Run e2e tests
	@pnpm test:e2e
install:
	@# Help: Install dependencies
	@pnpm install
update:
	@# Help: Update dependencies
	@pnpm update
audit:
	@# Help: Run audit tasks
	@pnpm audit
clean:
	@# Help: Clear dependencies
	@find . -type d -name "node_modules" -exec rm -rf {} +
	@find . -type d -name ".turbo" -exec rm -rf {} +
	@find . -type d -name ".svelte-kit" -exec rm -rf {} +		
run:
	@# Help: Run server
	@pnpm dev
lint:
	@# Help: Run linter
	@pnpm list
format:
	@# Help: Format code
	@pnpm format
build:
	@# Help: Build
	@pnpm build
