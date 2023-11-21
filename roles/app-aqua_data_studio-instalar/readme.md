# Descrição

Instala o Aqua Data Studio.

Para restaurar o backup adicionar a opção restaurar_backup no playbook:

Exemplo:
```yaml
  - role: app-aqua_data_studio-instalar
    restaurar_backup: true
```

# Dependências

## Coleções

## Funções

|Role|Task|
| :---: | :---: |
|commom|create_launcher<br>restore_configuration_files|
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
      datastudio:
        file: 'datastudio-16.0.5-9.tar.bz2'
        install_dir: 'datastudio-16.0.5-9'
        download_path: '{{downloads_path}}/sgbd/aquafold/'
```