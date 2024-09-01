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

	kubectl apply -f postgresdb/pg-deploy.yaml
	@echo "Postgresql applied successfully."

	kubectl apply -f postgresdb/pg-import-job.yaml
	@echo "Postgresql import applied successfully."

	kubectl apply -f py-crud-app-ds.yaml
	@echo "Python app deploy successfully."

delete:
	@echo "Delete in Kubernetes..."

	kubectl delete -f py-crud-app-ds.yaml
	@echo "Python app delete successfully."

	kubectl delete -f postgresdb/pg-deploy.yaml
	@echo "Postgresql uninstall successfully."

	kubectl delete -f postgresdb/pg-import-job.yaml
	@echo "Postgresql import job delete successfully."
	
	kubectl delete -f postgresdb/pg-password-secret.yaml
	@echo "Postgresql password secret delete successfully."

	kubectl delete -f postgresdb/pg-init-configmap.yaml
	@echo "Postgresql init configmap delete successfully."

	kubectl delete pvc postgres-data-postgresql-0
	@echo "PCV delete successfully."

	kubectl delete -f postgresdb/pv-local.yaml
	@echo "Persistent volume delete successfully."