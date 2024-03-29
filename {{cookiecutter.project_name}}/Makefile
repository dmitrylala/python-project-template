help:  ## Show help
	@grep -E '^[.a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}'

clean: ## Clean autogenerated files
	rm -rf dist outputs
	find . -type f -name "*.DS_Store" -ls -delete
	find . | grep -E "(__pycache__|\.pyc|\.pyo)" | xargs rm -rf
	find . | grep -E ".pytest_cache" | xargs rm -rf
	find . | grep -E ".ipynb_checkpoints" | xargs rm -rf
	find . | grep -E ".coverage*" | xargs rm -rf
	rm -f .coverage htmlcov

format: ## Run pre-commit hooks
	pre-commit run -a

sync: ## Merge changes from {{ cookiecutter.main_branch_name }} branch to your current branch
	git fetch -p
	git pull origin {{ cookiecutter.main_branch_name }}
	poetry install

update-dev: ## Update development dependencies
	poetry update --only dev
	poetry install

test: ## Run all tests
	pytest tests/test*.py
