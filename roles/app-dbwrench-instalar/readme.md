# Descrição

Instala e o Dbwrench

Para restaurar o backup adicionar a opção restaurar_backup no playbook:

Exemplo:
```yaml
  roles:
  - role: app-dbwrench-instalar
    restaurar_backup: true
```

# Dependências

## Coleções

## Funções

|Role|Task|
| :---: | :---: |
|commom|create_launcher|
| 

# Variáveis

## Vault

As variáveis que esta função precisa, devem ser colocadas no arquivo vault antes da executção do playbook:

```yaml
user:
  login: 
  group: 
downloads_path:
```

## Inventário

As variáveis que esta função precisa, devem ser colocadas no inventário antes da executção do playbook:

```yaml
    app:
      dbwrench:
        uri: 'https://dbwrench.com/download/files/v4'
        file: 'dbwrench.zip'
        download_path: '{{downloads_path}}/sgbd/dbwrench'
```