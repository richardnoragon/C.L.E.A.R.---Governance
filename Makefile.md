# C.L.E.A.R. Governance Makefile

SHELL := /bin/bash

.PHONY: help bootstrap check-structure list-standards new-standard new-adr lint-docs

help:
    @echo "C.L.E.A.R. Governance Tasks"
    @echo "  make bootstrap        # Create baseline repo structure (docs, roles, templates, etc.)"
    @echo "  make check-structure  # Validate presence of key governance files"
    @echo "  make list-standards   # List standards in templates/ and lifecycle/"
    @echo "  make new-standard     # Scaffold a new standard proposal"
    @echo "  make new-adr          # Scaffold a new ADR"
    @echo "  make lint-docs        # Run basic markdown checks (if tools available)"

bootstrap:
    @bash ./bootstrap_clear_repo.sh

check-structure:
    @test -f CHARTER.md || (echo "Missing CHARTER.md" && exit 1)
    @test -f SPEC.md || (echo "Missing SPEC.md" && exit 1)
    @test -d roles || (echo "Missing roles/ directory" && exit 1)
    @test -d templates || (echo "Missing templates/ directory" && exit 1)
    @test -d lifecycle || (echo "Missing lifecycle/ directory" && exit 1)
    @echo "Structure OK."

list-standards:
    @echo "Lifecycle specs:"
    @ls lifecycle || true
    @echo
    @echo "Standard templates:"
    @ls templates || true

new-standard:
    @read -p "Standard ID (e.g., STD-001): " ID; \
    read -p "Short name (kebab-case, e.g., logging-standard): " NAME; \
    FILE="standards/$${ID}-$${NAME}.md"; \
    mkdir -p standards; \
    if [ -f "$$FILE" ]; then echo "$$FILE already exists"; exit 1; fi; \
    cp templates/STANDARD_TEMPLATE.md "$$FILE"; \
    echo "Created $$FILE"

new-adr:
    @read -p "ADR ID (e.g., ADR-2026-001): " ID; \
    read -p "Short name (kebab-case, e.g., db-sharding): " NAME; \
    mkdir -p adr; \
    FILE="adr/$${ID}-$${NAME}.md"; \
    if [ -f "$$FILE" ]; then echo "$$FILE already exists"; exit 1; fi; \
    cp templates/ADR_TEMPLATE.md "$$FILE"; \
    echo "Created $$FILE"

lint-docs:
    @echo "Running basic markdown checks (if markdownlint is installed)..."
    @command -v markdownlint >/dev/null 2>&1 && markdownlint . || echo "markdownlint not installed; skipping."
