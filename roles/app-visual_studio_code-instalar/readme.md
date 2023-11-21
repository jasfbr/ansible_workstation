# Descrição

Instala o Visual Studio Code.

Para restaurar o backup adicionar a opção restaurar_backup no playbook:

Exemplo:
```yaml
  - role: app-visual_studio_code-instalar
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
backup_path:
downloads_path:
```

## Inventário

As variáveis que esta função precisa, devem ser colocadas no inventário antes da executção do playbook:

```yaml
    app:
      vscode:
        repository: 'https://packages.microsoft.com/repos/vscode stable main'
        key:
          uri: 'https://packages.microsoft.com/keys'
          file: 'microsoft.asc'
```