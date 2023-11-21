# Descrição

Instala o Spotify.

Para restaurar o backup adicionar a opção restaurar_backup no playbook:

Exemplo:
```yaml
  - role: app-spotify-instalar
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
```

## Inventário

As variáveis que esta função precisa, devem ser colocadas no inventário antes da executção do playbook:

```yaml
    app:
      spotify:
        repository: 'http://repository.spotify.com stable non-free'
        key:
          uri: 'https://download.spotify.com/debian'
          file: 'dbeaver.gpg.key'
```
