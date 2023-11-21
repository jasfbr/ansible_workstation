# Descrição

Instala o Apache Directory Studio

Para restaurar o backup adicionar a opção restaurar_backup no playbook:

Exemplo:
```yaml
  roles:
  - role: app-apache_directory_studio-instalar
    restaurar_backup: true
```

# Dependências

## Coleções

## Funções

|Role|Task|
| --- | --- |
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
      directory_studio:
        uri: 'http://dlcdn.apache.org/directory/studio/2.0.0.v20210717-M17'
        file: 'ApacheDirectoryStudio-2.0.0.v20210717-M17-linux.gtk.x86_64.tar.gz'
        path_download: '{{downloads_path}}/apache'
```