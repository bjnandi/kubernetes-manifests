# Makefile for applying an existing Kubernetes YAML file

# Apply the Secret to Kubernetes
apply:
	@echo "Applying to Kubernetes..."

	kubectl apply -f postgresdb/pv-local.yaml
	@echo "Persistent volume applied successfully."
	
	kubectl apply -f postgresdb/pg-password-secret.yaml
	@echo "Postgresql password secret applied successfully."

	kubectl apply -f postgresdb/pg-init-configmap.yaml
	@echo "Postgresql init configmap applied successfully."

	helm install postgresql bitnami/postgresql -f postgresdb/values.yaml
	@echo "Postgresql applied successfully."

	kubectl apply -f postgresdb/pg-import-job.yaml
	@echo "Postgresql import applied successfully."

delete:
	@echo "Applying to Kubernetes..."

	helm uninstall postgresql
	@echo "Postgresql uninstall successfully."

	kubectl delete -f postgresdb/pg-import-job.yaml
	@echo "Postgresql import job delete successfully."
	
	kubectl delete -f postgresdb/pg-password-secret.yaml
	@echo "Postgresql password secret delete successfully."

	kubectl delete -f postgresdb/pg-init-configmap.yaml
	@echo "Postgresql init configmap delete successfully.

	kubectl delete -f postgresdb/pv-local.yaml
	@echo "Persistent volume delete successfully."