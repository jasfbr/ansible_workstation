# Descrição

Instala e configura o Vim como editor padrão no shell.

Para restaurar o backup adicionar a opção restaurar_backup no playbook:

Exemplo:
```yaml
  - role: app-vim-instalar
    restaurar_backup: true
```

# Dependências

## Coleções

  - community.general

## Funções

|Role|Task|
| :---: | :---: |
|commom|restore_configuration_files|
| 

# Variáveis
As variáveis que esta função precisa, devem ser colocadas no arquivo vault antes da executção do playbook:

```yaml
user:
  login: 
  group: 
backup_path: 
```

## Inventário
