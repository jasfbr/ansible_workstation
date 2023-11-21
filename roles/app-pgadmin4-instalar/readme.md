# Descrição

Instala o PgAdmin4.

Para restaurar o backup adicionar a opção restaurar_backup no playbook:

Exemplo:
```yaml
  - role: app-nomachine-instalar
    restaurar_backup: true
```

# Dependências

## Coleções

## Funções

|Role|Task|
| :---: | :---: |
|commom|restore_configuration_files|
| 

# Variáveis

## Vault

As variáveis que esta função precisa, devem ser colocadas no arquivo vault antes da executção do playbook:

```yaml
user:
  login: 
  group: 
backup_path:
downloads_path:
```

## Inventário

As variáveis que esta função precisa, devem ser colocadas no inventário antes da executção do playbook:

```yaml
    app:
      pgadmin:
        repository: 'https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/{{ansible_distribution_release}} pgadmin4 main'
        key:
          uri: 'https://www.pgadmin.org/static'
          file: 'packages_pgadmin_org.pub'
```