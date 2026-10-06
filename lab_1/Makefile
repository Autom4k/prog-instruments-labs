FILE := lab1_var18.py
IN  ?= input.txt
OUT ?= output.txt

.PHONY: install run lint format format-check typecheck fullcheck precommit precommit-run clean

install:
	pip install -r requirements.txt

run:
	python $(FILE) $(IN) $(OUT)

lint:
	ruff check .

format:
	ruff check --fix .
	ruff format .

format-check:
	ruff format --check .

typecheck:
	pyright

fullcheck: lint format-check typecheck

precommit:
	cd .. && pre-commit install -c lab_1/.pre-commit-config.yaml --hook-type pre-commit --hook-type pre-push

precommit-run:
	cd .. && pre-commit run --all-files -c lab_1/.pre-commit-config.yaml

clean:
	python -c "import shutil; shutil.rmtree('.ruff_cache', ignore_errors=True); shutil.rmtree('__pycache__', ignore_errors=True)"
