# Descrição

Instala o Aqua Data Studio.

Para restaurar o backup adicionar a opção restaurar_backup no playbook:

Exemplo:
```yaml
  - role: app-dbeaver-instalar
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
      dbeaver:
        repository: 'https://dbeaver.io/debs/dbeaver-ce /'
        key:
          uri: 'https://dbeaver.io/debs/'
          file: 'dbeaver.gpg.key'
```